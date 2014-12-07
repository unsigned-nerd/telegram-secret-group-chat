telegram-secret-group-chat
==========================

An implementation of "secret group chat" for Telegram based on vysheng's telegram-cli.

Currently, the official telegram has secret chat feature for 1 to 1 conversation only.  It doesn't support secret chat for group chat yet.  To implement this, we use telegram-cli from vysheng (on github) and boonbot.lua from boonme (on github).

Terminology
===========
telegram: https://www.telegram.org/
telegram-cli: https://github.com/vysheng/tg/

Concepts
========
- Mr X works as a relay agent for Mr A, Mr B, Mr C and Mr D.
- Mr X creates a secret chat with Mr A, Mr B, Mr C and Mr D, separately.
- When Mr A sends message to Mr X, Mr X sends the message to Mr B, Mr C and Mr D over secret chat, separately.
- When Mr B sends message to Mr X, Mr X sends the message to Mr A, Mr C and Mr D over secret chat, separately.
- When Mr C sends message to Mr X, Mr X sends the message to Mr A, Mr B and Mr D over secret chat, separately.
- When Mr D sends message to Mr X, Mr X sends the message to Mr A, Mr B and Mr C over secret chat, separately.
- Mr A, Mr B, Mr C and Mr D can now chat securely in a group.

Features
========
- Ability to chat in a group using "telegram secret chat", aka "an implementation of telegram secret group chat" that works.
- Ability to send text message only.  For sending pictures, please wait for the next release.

Cautions
========
- TTL (burn it after reading / self-destruct timer) doesn't work yet.  You have to "clear history" by yourself.  Hopefully, vysheng (creator of telegram-cli) will fix it soon.

Technical details
=================
- Install telegram-cli.
- Starting from tg/test.lua (an example lua script from vysheng).
- We add our code into test.lua and the output is boonbot.lua
- Start booonbot by: telegram-cli -k tg-server.pub -s boonbot.lua

How to for newbies
==================
- Install telegram-cli from https://github.com/vysheng/tg/ .
- Assuming you install it under your home directory (~) so it is located at ~/tg/ .
- Get a new sim card (mobile phone number) which is dedicated for boonbot.
- Use the new sim card with a smart phone.  Install telegram on the phone and login (register) with your new sim card.
- From your telegram on smart phone, add your friends who will be added into the secret group chat.
- Start telegram-cli and login using that phone number.  Now I will call it boonbot.
- Use boonbot from telegram-cli to create secret chat with each of your friend.
- Quit boonbot.
- Download boonbot.lua .  I assume you place it at ~/boonbot.lua
- Edit boonbot.lua .  Search for "friend_list".  Replace Mr_A, Mr_B, Mr_C and Mr_D with your friends' usernames.  Please keep the "!_" as is.
- Start boonbot by: telegram-cli -k ~/tg/tg-server.pub -s ~/boonbot.lua
- Now, you send message to boonbot from Mr A, Mr B, Mr C and Mr D's smartphones and Enjoy! the secret group chat!!!
