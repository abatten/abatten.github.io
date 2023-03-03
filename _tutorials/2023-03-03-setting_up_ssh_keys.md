---
layout: page-fullwidth
title: "Setting up SSH Keys"
subheadline: "SSH Keys | Github | OzStar"
meta_teaser: "What are SSH Keys? Why do you need them? And how do you set them up?"
teaser: "What are SSH Keys? Why do you need them? And how do you set them up?"
header:
    image_fullwidth: "coding-header.jpg"
    title: ' '
    background-color: "#d97a73"
    caption: ' '
    caption_url: ' '
image:
    thumb:  tutorials/ssh/SSH_Logo.png
    homepage: tutorials/ssh/SSH_logo.png
    caption: ' '
    caption_url: ' ' 
categories:
    - tutorial
post_date: 2023-03-03
modify_date: 2023-03-03

permalink           : "/tutorials/setting_up_ssh_keys/"
---

<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->

<div class="medium-8 medium-pull-4 columns" markdown="1">

This tutorial is a summary of the *Cookies' n' Code* tutorial that I run every year at the
[Centre of Astrophysics and Supercomputing (CAS)](https://astronomy.swin.edu.au/) at the [Swinburne University of Technology](https://www.swinburne.edu.au/).
This tutorial aimed to get each PhD student to set up SSH keys on their computer and use them to log into the supercomputer. Due to this tutorial's origin, I often reference the OzSTAR supercomputer. However, any mention of 'OzSTAR' can be generalised to any other supercomputer or remote machine.

*Cookies' n' Code'* is a weekly coding group meeting at CAS, where students and postdocs discuss code and teach each other new things.

## TL;DR: Create an ssh-key, then copy it to the remote machine.

```bash
> ssh-keygen -t ecdsa -b 521
> ssh-copy-id username@hostname
```
Or, more specifically, if you have an account on OzSTAR Supercomputer with a `username`:
```bash
> ssh-keygen -t ecdsa -b 521
> ssh-copy-id username@ozstar.swin.edu.au
```
If you have already created ssh keys or have multiple ssh keys, you can specify which key you want using the `-i' flag:
```bash
> ssh-copy-id -i ~/.ssh/id_ecdsa.pub username@ozstar.swin.edu.au
```


## What do we mean by SSH?
Before we get to SSH Keys, let's clarify what we mean by *SSH*.
SSH stands for *Secure Shell*.

At the core of your computer's operating system, there is something called the *kernel*.
This program has 100% complete control over everything on your computer system, including how the CPU, GPU and memory is used.
Obviously, you, the humble user, shouldn't be able to mess with the kernel directly.
So instead, you can interact with the kernel indirectly through a *shell*.
A shell is essentially the middle point between you and the kernel, like a protective layer around the kernel.
You can type a command into a shell, and it will talk to the kernel and ask it to perform the task.

The prompt in your terminal is a shell.
The most famous shell, and possibly the shell you use, is called: `BASH` (Bourne Again SHell). Other examples include: `ZSH`, `TSH`, `CSH`, etc.
So when you use a terminal, you use a shell to communicate with the kernel on your computer.

However, if you want to connect to another computer and use its kernel (i.e. a supercomputer), you need a way to communicate to its shell and, ideally, do that securely.
So when you securely connect to another machine's shell, you do it via a Secure Shell method: SSH.

## What is an SSH Key?
SSH keys prove who you are to a remote machine. This would be similar to proving who you are with a username and a password.
If a user has a correct username and password, they will likely be truthful about who they are.
Similarly, users with the correct SSH keys are even more likely to be who they say they are.

SSH keys always come in pairs, and they are a pair of encrypted numbers that are saved in different text files.
Every pair consists of a *private key* and a *public key*. If these keys are on a remote machine, they are called 'host keys'.
If these keys are on your local machine, they are called 'user keys'.

SSH keys work by supplying a public key to a remote machine and using the matching private key to authenticate any information encrypted with the public key.

As an analogy, imagine that the public key is a padlock, and the private key is the only copy of the key that can open that lock.
In this analogy, you can imagine that you not only have one padlock, but you can make as many copies of the padlock as you'd like
and give them to anyone that you'd like to send you encrypted information. But you only have one copy of the key that opens all of the locks.

If you give a remote machine one of these padlocks (or public keys), it can encrypt (or 'lock') information and data with that padlock.
Then you can prove who you are by decrypting (or 'unlocking') that information with your private key since you can only open the locks.

This is the basics of how you can 'prove' your identity with SSH keys. Basically, you are proving you are with the existence of a particular file on your computer.

## Why should you care about SSH Keys?

#### 1. SSH keys make the login process more straightforward.
Instead of authenticating logins with just passwords and usernames, you can use a matching set of SSH keys to prove who you are.
This means you can use only SSH keys if you wish and not be required to enter usernames and passwords whenever you want to access a remote machine.

#### 2. More secure than passwords.
Typically we as humans make bad passwords. Reusing old, easy-to-crack passwords or writing them down is a security risk.
A typical SSH key is more secure than a password as it is essentially a very large number that is encrypted.
You can also add a *passphrase* to your SSH keys to provide extra security if needed.
Adding a passphrase means using a password and the SSH key to access the remote machine.

### 3. Sometimes required for specific tasks or services.
Some systems require the user to supply a public key (for example, Github) to access the service.
This means you must set them up to even use the service, so you could use them on other machines too.


## Creating an SSH key pair.
Okay, now let's make our SSH key pair. For this, we are using `ssh-keygen`.
```bash
> ssh-keygen -t ecdsa -b 521
```
Here we are creating an ESDCA encrypted SSH key pair with 521 bits.
See below for where these files are stored.

When you do this, it will ask you if you'd like to make a 'passphrase'.
This is essentially adding a password to your SSH keys.
So whenever your SSH key is used, you must also provide the passphrase.
If you don't want to add a passphrase, leave it blank and press <ENTER> or <RETURN>.


## Copying your public key to a remote machine.
Now that you have created your SSH key pair, you must copy your public key to the remote machine.
This is like giving someone your padlock so they can encrypt information that only you can unlock.

To copy the public key, you must know your `username` and that machine's hostname'.
```bash
> ssh-copy-id username@hostname
```
If you are a user of the OzSTAR Supercomputer at Swinburne University of technology, this will take the following form:

```bash
> ssh-copy-id username@ozstar.swin.edu.au
```
If you want to specify which public key you would like to copy (e.g. you have created more than one key pair), you can do so with the `-i' flag:

```bash
> ssh-copy-id -i ~/.ssh/id_ecdsa.pub username@ozstar.swin.edu.au
```

If you want to copy your SSH key to Github, you can see [their tutorial here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).


## Your ~/.ssh directory and the SSH config file.
Your public and private keys are stored in your `~/.ssh` directory by default.
This is the directory that also contains all of your SSH information.
If you `ls` in your `~/.ssh` directory, you should see some or all of these files.
```bash
> ls ~/.ssh
config    id_ecdsa     id_ecdsa.pub    known_hosts
```
These files are the following:
- `config` - This is your SSH configuration file. See below for more information
- `id_ecdsa` - This is your private SSH key. DO NOT SHARE THIS FILE. Do not upload this file anywhere or
If you accidentally share or upload this file, delete it and your public keys from your known hosts, then create new key pairs.
- `id_ecdsa.pub` - This is your public SSH key, and this is the file that gets copied to the remote machine.
- `known_hosts` - This file lists known remote machines.


### The SSH config file
The SSH config file contains information what
If you do not have a config file, you can create one, and you can add something like the following:
```
Host ozstar
  HostName ozstar.swin.edu.au
  User <username>
  ForwardX11 yes
  ForwardAgent yes

Host github.com
 IdentityFile ~/.ssh/id_ecdsa
```
- `Host` - The name you want to call the host machine. With this, you can ssh into the machine with just `ssh <Host>` (e.g. `ssh ozstar`).
- `HostName` - The HostName of the remote machine. (e.g. `ozstar.swin.edu.au`)
- `User` - Your username on the remote machine.
- `ForwardX11` - Enable/Disable X11 forwarding. If you enable X11 forwarding, screens, images, and displays on the remote machine will be displayed on your computer. This is necessary to open images or programs with windows on a remote machine (e.g. OzSTAR).
- `ForwardAgent` - Enable/Disable Agent forwarding. Enabling Agent forwarding lets you use your SSH keys on a remote machine.
For example: If you want to `git pull` some code from Github whilst, on a remote machine like OzSTAR, you can use your Github SSH keys without copying them to OzSTAR first.
This is good if you don't want to leave personal information or keys on a remote machine.
- `IdentityFile` - Specify a private key file with the user's Identity Key' to be read when using a public key authentication.

Now if you have set up your SSH keys and config file, you should be able to log into the remote machine with just `ssh host`. For example:

```bash
ssh ozstar
```

