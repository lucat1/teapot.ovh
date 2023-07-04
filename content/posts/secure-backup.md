+++
title = "Setup the Matrix Secure Backup for your encrypted chats"
author = "Teapot admin"
date = "2023-01-23"
description = "A short guide to safely save your encryption token to recover chats in case of device loss"
+++

# Why

In Matrix encryption keys are stored on the devices itself. Each connection has
its own key and they get shared across all your (online) sessions when a new
one is used. In the case of theft or hardware failure of a device that has not
shared its keys with anyone, or worse yet, your only device, you will either
lose the contents of some chats or be unable to ready anything at all.

Now, that's bad. To prevent this, and also to improve the key sharing feature
when your other devices are offline it is important that you enable Secure Backup.

What this does is it keeps all your keys on your homeserver, safely encrypted
with a passphrase. When you log-in from another device, you can first of all
trust it without another device being online: proving you can decrypt the backup
is enough to provide your identity. Secondly, the keys for your new session will
be automatically backed-up and the ones from all your previous sessions will be
imported, so you can read your precious encrypted message history.

If you don't feel safe this way, you can always manually export the keys from
each session you use to a file (via Settings > Security & Privacy > Cryptography > export E2E room keys)
and manually import then on a new device. It's the same exact process, albeit
more tedious, but nothing gets stored on teapot.ovh.

# How

Enabling Secure Backup is as simple as it gets. After logging in, in a secure
session, go to your Settings > Security & Privacy > Secure Backup and click on
"Set up". In the dialog, chose "Enter Security Passphrase". The other option is
just as safe, but less convenient. You'll be prompted twice for a security
passphrase. It's recommended to use a different password from your usual login one.
Next, _save_ the generated Security Key somewhere safe, along with your password.

When needed, you'll be asked for your passphrase first. Failing to recall it you
can use the Security Key. _Please_, put these somewhere safe, such as in a
password manager. You don't want to lose these!
