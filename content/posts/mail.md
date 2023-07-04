+++
title = "Connect to your mail box"
author = "Teapot admin"
date = "2023-03-20"
+++

To connect to your mail box you can use these settings on your favourite mail
client. Our server uses SMTPS and IMAPS for comunication.

- Incoming server:
  | Option | Value |
  |---------|-----------------|
  | Protocol | IMAP(s) |
  | Hostname | `mail.teapot.ovh` |
  | Port | `993` |
  | Connection Security | SSL/TLS |
  | Authentication method | Normal Password |
  | Username | `user@teapot.ovh` [^1] |

- SMTP configuration:
  | Option | Value |
  |---------|-----------------|
  | Protocol | SMTP(s) |
  | Hostname | `mail.teapot.ovh` |
  | Port | `587` |
  | Connection Security | STARTTLS |
  | Authentication method | Normal Password |
  | Username | `user@teapot.ovh` [^1] |

[^1]: replace `user` with your username.
