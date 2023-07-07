+++
title = "Upload your static website"
author = "Teapot admin"
date = "2023-07-04"
+++

Teapot now offers a static site hosting functionality. As one of our users, you
can upload static files to one of our machines and have them served under either
`teapot.ovh/~$user` or `teapot.ovh/@$user`. In order to do so,
you must first establish an SSH connection to our `proxy` machine. This is the
same instance which holds the HTTP server proxying all our traffic. In fact,
the server serving your static files will be the same reverse proxy software.
To connect to `proxy` you can use the following SSH config:

```ssh
Host honey
  HostName honey.teapot.ovh
  Port 2222
  User $user

Host proxy
  HostName 192.168.1.100
  User $user
  ProxyJump honey
```

Mind replacing `$user` with your username. It should match the one you have on
matrix. Authentication is handled via ssh keys. Please contact the administrator
to provide a source for your keys and get your account set-up.

Once you have an account and the configuration is in place, a simple `ssh proxy`
shall prompt you twice for your key's password and then let you in. On this
machine your user does have an home, but please, keep in mind that space is
limited. You can use this home as a scratchpad where you can compile your
website though, as shown in [a later example](#building-a-hugo-website).

Your website files shall live under `/var/www/sites/$user`. You can upload
files effortlessly via either `rsync` (suggested) or `scp` (deprecated):

```sh
$ rsync -rav ./your_site/ proxy:/var/www/sites/$user
```

Mind the trailing slash after `your_site`. When `rsync` sees that, it copies
the folders contents and not the folder itself. If you forget it, your site may
live under `teapot.ovh/~$user/your_site` and you'll have some finessing to do
in the shell in order to get the files in the correct place.

If you've done it correctly, your site or your files should be available under
`teapot.ovh/~$user` or `teapot.ovh/@$user`.

The whole `/var/www/sites` folder is 32Gib, so you do have plenty of space for
your site. Please be mindful of what you upload, as the disk quota is shared
with all the other users!

All files must be `chowned` to `$user:caddy` and have a permission of at least
`+r` for the group.  To achieve this you can use:
```sh
$ chown -R $user:caddy /var/www/sites/$user
$ chmod -R 750 /var/www/sites/$user
```

## Building a hugo website

The command line for the `hugo` website builder is available on the `proxy`
machine. Therefore, you can use it, alongside with your home folder or `/tmp`,
to build your static website right on the machine. You could develop and
automate a script which does something akin to the following:

```sh
$ rm -rf /var/www/site/$user/* /var/www/site/$user/.*
$ git clone git@codeberg.org:user/site.git
$ cd site
$ hugo --destination /var/ww/site/$user
$ rm -rf site
```

A simple improvement could also involve not cloning the repository every time,
just pulling from it instead. Ideally, a trivial `ansible` playbook could be used.
