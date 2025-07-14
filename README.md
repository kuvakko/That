#const settings = {
  packname: 'MAKUDI DAS',
  author: '‎',
  botName: "MAKUDI DAS",
  botOwner: 'Professor', // makudi das
  ownerNumber: '91 7034763045', //here without + symbol, just add country code & number without any space
  giphyApiKey: 'qnl7ssQChTdPjsKta2Ax2LMaGXz303tq',
  commandMode: "public",
  description: "This is a bot for managing group commands and automating tasks.",
  version: "2.0.6",
};

const settings = {
  packname: 'MAKUDI DAS',
  author: '',
  botName: "MAKUDI DAS",
  botOwner: 'Professor', // makudi das
  ownerNumber: '917034763045', // Country code + number, no spaces
  giphyApiKey: 'qnl7ssQChTdPjsKta2Ax2LMaGXz303tq',
  commandMode: "public",
  description: "This is a bot for managing group commands and automating tasks.",
  version: "2.0.6",
};

module.exports = settings;
 const { default: makeWASocket, useMultiFileAuthState } = require("@whiskeysockets/baileys");

async function startBot() {
    const { state, saveCreds } = await useMultiFileAuthState("auth_info");
    const sock = makeWASocket({ auth: state });

    sock.ev.on("messages.upsert", async ({ messages }) => {
        const msg = messages[0];.Remov
        if (!msg.message) return;groupParticipantsUpdate(groupJid, [userJid], "remove")

        const text = msg.message.conversation;
        const groupJid = msg.key.remoteJid;

        if (text && text.startsWith("!remove")) {
            const userNumber = text.split(" ")[1];
            const userJid = userNumber + "@s.whatsapp.net";
            await sock.groupParticipantsUpdate(groupJid, [userJid], "remove");
            await sock.sendMessage(groupJid, { text: `Removed ${userJid}` });
        }
    });

    sock.ev.on("creds.update", saveCreds);
}

startBot();
