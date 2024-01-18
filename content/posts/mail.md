+++
title = "Connect to your mailbox"
author = "Teapot admin"
date = "2024-01-18"
+++

To connect to your mailbox you can use these settings on your favourite mail
client. Our server uses SMTPS and IMAPS for communication.

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

# Mail sorting

As per RFC5233[^2] our mail server supports so-called subaddressing. That is,
when you receive an email at `key+user@teapot.ovh`, the `key` part does not
make up part of your username, but instead is considered as "detailed addressing".
Our mail server uses this additional information to automatically sort your
incoming mail in different folders based on this prefix[^3].

When the user `user` receives email at the address `key+user@teapot.ovh`, this
message will be stored in the `Sorted/Key` folder (please mind, the
automatic capitalization of `key`). If such a folder is not available at the
moment of delivery, the system will automatically create it.

## Subscribing to Sorted Folders

By default, most mail clients don't the these folders. While the configuration
depends on the mail client being used, here are the steps required to show and
actively synchronize the Sorted Folders in Mozzilla Thunderbird:

0. Add your mail account as detailed earlier.
1. Right-click on the mailbox in your navbar, and select `Subscribe`.
2. Tick all the folders you are interested in subscribing to, including any
folder under `Sorted/`. If they don't show up, you can hit `Refresh`.
3. Click `OK`. You should see the selected folders appear on the left-hand side.
4. Although you can see the folders now, they are not synchronized by default.
To fix that, you can right-click on each folder and select `Properties`. In the
pop-up, tick `When getting new messages for this account, always check this folder`.
Then finally save your changes by clicking `OK`.

[^1]: replace `user` with your username.
[^2]: Sieve Email Filtering: Subaddress Extension, read more on
[IETF's website](https://datatracker.ietf.org/doc/html/rfc5233). 
[^3]: NOTE: our configuration allows also the usage of the `-` character in place
of the `+`, for use with nasty services which don't allow the standard character
in the mail address.
