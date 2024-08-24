# Modern Whatsapp Bot - Alpha

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WhatsApp Bot - Alpha</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/4.0.0/socket.io.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 20px;
        }
        #bot-container {
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
        }
        #message-input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        #send-button {
            padding: 10px 15px;
            background-color: #25D366;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div id="bot-container">
    <h1>WhatsApp Bot - Alpha</h1>
    <input type="text" id="message-input" placeholder="Type your message here...">
    <button id="send-button">Send</button>
</div>

<script>
    const socket = io('https://your-server-url.com');

    document.getElementById('send-button').addEventListener('click', function() {
        const message = document.getElementById('message-input').value;
        socket.emit('sendMessage', message);
        document.getElementById('message-input').value = '';
    });

    socket.on('receiveMessage', function(message) {
        console.log('New message:', message);
    });
</script>

</body>
</html>
