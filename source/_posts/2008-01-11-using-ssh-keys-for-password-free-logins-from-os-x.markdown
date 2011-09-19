---
date: 2008-01-11 18:05:57
title: Using SSH Keys for Password-Free Logins from OS X
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2008/01/using-ssh-keys-for-password-free-logins-from-os-x/
---
If your remote username is different from your OS X username, edit your `~/.ssh/config` file like so:

    Host whathaveyou.com
        User remote_username

### Generating your keys

On your OS X machine, enter this command:

    ssh-keygen

Enter a password or don't (I didn't).

This creates a public (`~/.ssh/id_rsa.pub`) and private key (`~/.ssh/id_rsa`).

### Copying the public key to the remote server

Log in to the server with ssh (with your password--for the last time).

However you want to do it, open the file `~/.ssh/authorized_keys` on the remote server and paste in the contents of `id_rsa.pub`. Alternately, you could use `scp` like so:

    scp ~/.ssh/id_rsa.pub remote_username@whathaveyou.com:~/.ssh/authorized_keys

(Naturally, if the file and/or folder aren't there, you'll have to create them first.)

Now change the permissions:

    chmod 700 ~/.ssh/
    chmod 600 ~/.ssh/authorized_keys

All done.  The next time you want to ssh to the server, it won't prompt you for a password.

### Sources:

* Correspondence with [Jason](http://www.workingwithrails.com/person/6187-jason-t-johnson) and [Scott](http://sitening.com/about/scott/).
* [Geek Times](http://www.geektimes.com/macintosh/os/x/10_3/and/ssh_keygen.html "Mac OS X: ssh key generation and deployment")
* [Rails Machine](https://support.railsmachine.com/index.php?pg=kb.page&amp;id=33)

