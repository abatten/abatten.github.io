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
This tutorial is a summary of the *Cookies 'n' Code* tutorial that I run every year at the 
[Centre of Astrophysics and Supercomputing (CAS)](https://astronomy.swin.edu.au/) at the [Swinburne University of Technology](https://www.swinburne.edu.au/).
The purpose of this tutorial was to get each of the PhD students to set up SSH keys on their computer, and use them to log into the Supercomputer. Due to the origin of this tutorial, I often make reference to the OzSTAR supercomputer. However, any mention of 'OzSTAR' can be generalised to any other supercomputer or remote machine.

*Cookies 'n' Code'* is a weekly coding group meeting at CAS, where people get together to discuss code and teach each other new things.

## TL;DR: Create a ssh-key, then copy it to the remote machine.

```bash
> ssh-keygen -t ecdsa -b 521
> ssh-copy-id username@hostname
```
Or more specifically if you have an account on OzSTAR Supercomputer with a `username`:
```bash
> ssh-keygen -t ecdsa -b 521
> ssh-copy-id username@ozstar.swin.edu.au
```
If you have already created ssh keys, or have multiple ssh keys, you can specify which key you want using the `-i` flag: 
```bash
> ssh-copy-id -i ~/.ssh/id_ecdsa.pub username@ozstar.swin.edu.au
```


## What do we mean by SSH?
Before we get to SSH Keys, lets just clarify what we mean by *SSH*. 
SSH stands for *Secure Shell*.

At the core of your computers operating there is something called the *kernel*. 
This is basically a program that has 100% complete control over everything on your computer system, including how the CPU, GPU and memory is used.
For obvious reasons, you, the humble user, shouldn't be able to mess with the kernel directly.
So instead, you can interact with the kernel indirectly, through a *shell*.
A shell is basically the middway point between you and the kernel, sort of like a protective layer around the kernel.
You can type a command into a shell, and it will talk to the kernel and ask it to perform the task.

The prompt in your terminal is a shell.
The most famous shell, and possibly the shell you use is called: `BASH` (Bourne Again SHell). Other examples include: `ZSH`, `TSH`, `CSH`, etc.
So when you use a terminal, you are using a shell to communicate with the kernel on your computer.

However, if you want to conenct to another computer, and use its kernel (i.e. maybe a supercomputer), you need a way to connect to its shell, and ideally, do that securely.
So when you securely connect to another machines shell, you do it via a Secure Shell method: SSH.

## What is an SSH Key?
SSH keys are used to essentially prove who you are to a remote machine. This would be similar to proving who you are with a username and a password.
If a user has a correct username and a password, they are likely to be truthful about who they are. 
Similarly, if a user has the correct SSH keys, they are even more likely to be who they say they are.

SSH keys always come in pairs, and they are a pair of encrypted numbers that are saved in different text files.
Every pair consists of a *private key* and a *public key*. If these keys are on a remote machine they are refered to as 'host keys'.
If these keys are on your local machine they are refered to as 'user keys'.

SSH keys work by supplying a public key to a remote machine, and using the matching private key to authenticate any information encrypted with the public key.

As an analogy, imagine that the public key is a padlock, and the private key is the only copy of the key that can open that lock. 
In this analogy, you can imagine that not only do you have one padlock, but you can make as many copies of the padlock as you'd like 
and can give to any one that you'd like to send you encrypted information. But you only have one copy of the key that opens all of the locks.

If you give a remote machine one of these padlocks (or public keys) it is then able to encrypt (or 'lock') information and data with that padlock.
Then you are able to prove who you are by decrypting (or 'unlocking') the that information with your private key since you ar ethe only person with the ability open the locks.

This is the basics of how you can 'prove' your identity with SSH keys. Basically you are proving you are with the existance of a very specific file on your computer.

## Why should you care about SSH Keys?
There are three main avenues you might try to autheticate if someone is their
There a quite a few reasons why you might want 


#### 1. SSH keys makes the login process easier.
Instead of authenticating logins with just passwords and usernames, you can instead use the existance of a matching set of SSH keys to prove who you are.
This means, you can decide to use only SSH keys if you wish and not be required to enter usernames and passwords every time you want to access a remote machine.

#### 2. More secure than passwords.
Typically we as humans make bad passwords. Reusing old passwords, easy to crack passwords, or just writing them down is a secutiry risk. 
A typical SSH key is more secure than a password as it is essentially a very large number than is encrpyted. 
Additionally, you can also add a *passphrase* to your SSH keys to provide extra security if you need it. 
Adding a passphrase means you would been both a password and the SSH key to access the remote machine.

### 3. Sometimes required for specific tasks or services.
There are some systems that require the user to supply a public key (for example Github) to have access to the service.
This means you must set them up to even use the service, so you might as well use them on other machines too.


## Creating an SSH key pair.
Okay, now lets make our SSH key pair. For this we are using `ssh-keygen`.
```bash
> ssh-keygen -t ecdsa -b 521
```
Here we are creating an ESDCA encrypted SSH key pair with 521 bits.
See below for where these files are stored.

When you do this is will ask you if you'd like to make a 'passphrase'. 
This is essentially adding a password to your SSH keys. 
So whenever your SSH key is used, you will also have to provide the passphrase. 
If you don't want to add a passphrase, you can just leave it blank and press <ENTER> or <RETURN>.


## Copying your public key to a remote machine.
Now that you have created your SSH key pair, you will need to copy your public key to the remote machine.
This is like giving someone your padlock so they can encrypt information with it that only you can unlock.

To copy the public key, you will need to know your `username` and the `hostname` of that machine.
```bash
> ssh-copy-id username@hostname
```
If you are a user of the OzSTAR Supercomputer at Swinburne University of technology this would take the following form:

```bash
> ssh-copy-id username@ozstar.swin.edu.au
```
If you want specify which public key you would like to copy (e.g. you have created more than one key pair), you can do so with the `-i` flag:

```bash
> ssh-copy-id -i ~/.ssh/id_ecdsa.pub username@ozstar.swin.edu.au
```

If you would like to copy you SSH key to Github you can see [their tutorial here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).


## Your ~/.ssh directory and the SSH config file.
You public and private keys are stored in your `~/.ssh` directory by default.
This is the directory that also contains all of your SSH information.
If you `ls` in your `~/.ssh` directory you should see some or all of these files.
```bash
> ls ~/.ssh
config    id_ecdsa     id_ecdsa.pub    known_hosts
```
These files are the following:
- `config` - This is your SSH configuration file. See below for more information
- `id_ecdsa` - This is your private SSH key. DO NOT SHARE THIS FILE. Do not upload this file anywhere or
If you accidently share or upload this file, delete it, and your public keys from all of your known hosts, then create new key pairs.
- `id_ecdsa.pub` - This is your public SSH key. This is the file that gets copied to the remote machine.
- `known_hosts` - This file is a list of known remote machines.


### The SSH config file
The SSH config file contains information what 
If you dont have a config file, you can create one and you can add something like the following:
```
Host ozstar
  HostName ozstar.swin.edu.au
  User <username>
  ForwardX11 yes
  ForwardAgent yes

Host github.com
 IdentityFile ~/.ssh/id_ecdsa
```
- `Host` - The name you want to call the host machine. With this you'll be able to ssh into hte machine with just `ssh <Host>` (e.g. `ssh ozstar`).
- `HostName` - The HostName of the remote machine. (e.g. `ozstar.swin.edu.au`) 
- `User` - Your username on the remote machine.
- `ForwardX11` - Enable/Disable X11 forwarding. If you enable X11 forwarding, screens, images, displays that appear on the remote machine will be displayed on your computer. This is necessary if you want to open images or programs that have windows on a remote machine (e.g. OzSTAR).
- `ForwardAgent` - Enable/Disable Agent forwarding. Enabling Agent forwarding lets you use your personal SSH keys whilst on a remote machine. 
For example: If you want to `git pull` some code from Github whilst on a remote machine like OzSTAR, you can use your personal Github SSH keys without having to copy them to OzSTAR first. 
This is good if you dont' want to leave personal information or keys on a remote machine. 
- `IdentityFile` - Specify a private key file that has the users 'Identity Key' to be read when using a public key authentication.

Now if you have set up your SSH keys and config file, you should be able to log into the remote machine with just `ssh host`. For example:

```bash
ssh ozstar
```
