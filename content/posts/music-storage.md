+++
title = "Connect to the music storage"
author = "Teapot admin"
date = "2023-01-29"
+++

To connect to your music storage on our infrastructure you should add the
following to your ssh config located in `~/.ssh/config`:

```ssh
Host honey
  HostName honey.teapot.ovh
  Port 2222
  User $user

Host music
  HostName 192.168.1.102
  User $user
  ProxyJump honey
```

Mind replacing `$user` with your username. It should match the one you have on
matrix. Authentication is handled via ssh keys. Please contact the administrator
to provide a source for your keys and get your account set-up.

Once you have an account and the configuration is in place, a simple `ssh music`
shall prompt you twice for your key's password and then let you in.

You can place your content in `/music/$user` so it will be properly indexed by
the Music Server. The [`tagger`](https://codeberg.org/lucat1/tagger) utility
shall be available in your path and it is the suggested music tagger.
