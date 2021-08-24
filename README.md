# Discord-Bot
Discord es una aplicación de chat que permite a millones de usuarios de todo el mundo transmitir mensajes y voz en línea en comunidades llamadas gremios o servidores. Discord también proporciona una amplia API que los desarrolladores pueden usar para crear potentes bots de Discord. Los bots pueden realizar diversas acciones, como enviar mensajes a servidores, mensajes directos a usuarios, moderar servidores y reproducir audio en los chats de voz.
![image](https://user-images.githubusercontent.com/29583728/130670222-e6a5c64c-f59f-4fbf-bccf-bb44084de648.png)

Al parecer Discord mato a mi bot XD
![image](https://user-images.githubusercontent.com/29583728/130670327-7bf46e16-e785-4039-b236-b4b0febc8492.png)

indes.js: 
const { Client, Intents } = require('discord.js');
const client = new Client({ intents: [Intents.FLAGS.GUILDS, Intents.FLAGS.GUILD_MESSAGES] });
const config = require("./config.json");

client.login(config.BOT_TOKEN)
const prefix = "!";
client.on("message", function(message) {
    if (message.author.bot) return;
    if (!message.content.startsWith(prefix)) return;
        const commandBody = message.content.slice(prefix.length);
        const args = commandBody.split(' ');
        const command = args.shift().toLowerCase();
    if (command === "ping") {
        const timeTaken = Date.now() - message.createdTimestamp;
        message.reply(`Pong! This message had a latency of ${timeTaken}ms.`);
    }
    else if(command === "sum"){
        const numArgs = args.map(x => parseFloat(x));
        const sum = numArgs.reduce((counter, x) => counter += x);
            message.reply(`The sum of all the arguments you provided is ${sum}!`);
    }
})


