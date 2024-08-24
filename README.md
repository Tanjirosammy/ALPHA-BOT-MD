# Modern Whatsapp Bot with Image by Name Alpha

const { Client, MessageMedia } = require('whatsapp-web.js');
const qrcode = require('qrcode-terminal');
const fs = require('fs');

// Initialize the client
const client = new Client();

// Generate QR code for authentication
client.on('qr', (qr) => {
    qrcode.generate(qr, { small: true });
});

// On successful authentication
client.on('ready', () => {
    console.log('Client is ready!');
});

// Function to send an image by name
const sendImageByName = (chatId, imageName) => {
    const media = MessageMedia.fromFilePath(`./images/${imageName}`);
    client.sendMessage(chatId, media);
};

// Example usage
client.on('message', message => {
    if (message.body === '!sendImage') {
        sendImageByName(message.from, 'alpha_image.jpg');
    }
});

// Start the client
client.initialize();
