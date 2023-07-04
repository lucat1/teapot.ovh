+++
title = "Setup the Matrix Bridges"
author = "Teapot admin"
date = "2023-01-22"
description = "A guide to the initial configuration of the matrix bridges provided by Teapot"
+++

# Introduction

This short article will teach you how to initially configure the matrix bridges
offered by [teapot.ovh](https://element.teapot.ovh). Currently, only bridges for
Telegram and WhatsApp are provided.

# WhatsApp

In order to bridge your messages with your Telegram account you just have to login.
Make sure you open the app at least once every 20 days as otherwise the session
used by your matrix bridge will be terminated.

Now, open your chat with the bot[^1] and type `login`. When propted, scan the QR
code the bot sent you with your WhatsApp client on your mobile.

After a successful login the bridge will start backflling all your chats
and contacts. Chats _should_ be filled with up to three moths of history.
This process will craete both groups and PM rooms for all your whatsapp contacts.
Please, be patient as this can take a few hours. At any time you can verify the
bridge is still connected with WhatsApp by issuing the `ping` command.

# Telegram

As for WhatsApp, only a login with your Telegram mobile app is required.
Open you chat with the bot[^1] and type `login`. When asked to, insert your phone
number, including the prefix for your country. Assuming my number is `+42 543 9348 546`
I would reply with `425439348546`.

When successful, the bridge will notify you that it was able to log-in on your
behalf and will start syncing all the chats. Please, be patient as this can take
a few hours. This process will only create rooms for your group chats, while PM
rooms will be instantiated on first message. After the initial sync, if you want
to chat with a telegram contact but a room is not available yet feel free to
start a new chat with the telegram account on Matrix and the bot will
automatically take care of the briding. At any time you can verify the bridge
is still connected with Telegram by issuing the `ping` command.

# Common steps

_This steps applies to all the provided bridges_.

After you've successfully logged into your third-party account, double
puppeteering shall be enabled by default and set-up automatically.

You can verify that by send a `ping-matrix` command to the appropriate bot [^1].

[^1]:
    The currently available bridges can be contacted at the following addresses:

    - [@telegrambot:teapot.ovh](https://matrix.to/#/@telegrambot:teapot.ovh)
    - [@whatsappbot:teapot.ovh](https://matrix.to/#/@whatsappbot:teapot.ovh)
