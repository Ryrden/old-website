---
layout: post-en
title: SSH key on github - Windows and Linux
seo_title: How to Generate and Add an SSH Key to GitHub - Secure Authentication Guide
seo_description: 'Learn how to generate and add an SSH key to GitHub for secure authentication. Follow our step-by-step guide with detailed instructions for Linux and Windows users. Configure your SSH key on GitHub to enable push and pull operations effortlessly, without repeated authentication. Optimize your GitHub experience now!'
excerpt: Step-by-step guide on generating and adding an SSH key to GitHub for secure authentication. Learn how to create SSH keys using the ED25519 algorithm with detailed instructions for Linux and Windows. Configure your SSH key on GitHub to enable push and pull operations without repeated authentication.
cover_image: 'https://i.imgur.com/9GC9TvD.webp'
canonical_url: 'https://ryrden.github.io/old-website/en/2023-04-17-github-ssh-en'
image_alt: 'A statue of an oktokat (github mascot) in the center, in the background a laptop with the main page of GitHub open.'
tags:
  - github
  - ssh
  - linux
  - windows
author: Ryan Souza
devto_url: 'https://dev.to/ryrden/ssh-key-on-github-windows-and-linux-877'
tabnews_url: null
locale: en_US
lang: en
comments: true
published: true
id: 1718348
date: '2024-01-05T15:41:34Z'
---

- [What is a SSH Key?](#what-is-a-ssh-key)
- [Generating a SSH Key](#generating-a-ssh-key)
  - [Linux](#linux)
  - [Windows](#windows)
- [References](#references)

## What is a SSH Key?

An SSH key is a pair of keys used to authenticate a user on a server. The public key is used to encrypt data, and the private key is used to decrypt it. The public key is shared with the server, while the private key is kept secret by the user.

There are various encryption algorithms to generate SSH keys, but in this tutorial, I will teach you how to generate an SSH key using the ED25519 algorithm. ED25519 is an elliptic curve digital signature algorithm considered secure and fast.

To learn more about this topic, I recommend this article from Teleport: [Article](https://goteleport.com/blog/comparing-ssh-keys/) (in English)

## Generating a SSH Key

From now on, I will divide this tutorial into two parts, one for Linux and another for Windows.

Before you start, you need to have Git installed on your machine. If you don't, I recommend the official Git documentation to install Git on your machine: [Documentation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

### Linux

To generate an SSH key on Linux, you need to open the terminal and type the following command:

```bash
ssh-keygen -t ed25519 -C <your-email>
```

![ssh-keygen on linux](https://i.imgur.com/J56UKtq.webp)

After typing the command, you will be prompted to fill in some information, such as the key name and password. You can type any name as long as you don't forget it; in my case, I just pressed `enter` so that Git would automatically generate the key name and have no password.

With the key generated, you should copy the public key to the clipboard. For this, navigate to the folder where the key was generated (by default it is in the `~/.ssh` folder, as shown in the previous image) and type the following command:

```bash
cat id_ed25519.pub
```

and copy the key that appears on the screen.

Now you need to go to the GitHub settings page and add the key you just copied.

here a shortcut for you to go directly to the GitHub SSH keys settings page: [SSH Keys Settings Page](https://github.com/settings/keys)

here you should go to `New SSH key` and paste the key you copied earlier.

![paste key on github - linux](https://i.imgur.com/5L6KrD8.webp)

By clicking on Add SSH key, you will add the SSH key to GitHub.

Now, just test if the key was added correctly and clone any repository you have access to, always using the SSH address. To test if the key was added correctly, you can type the following command:

```bash
ssh git@github.com
```

if everything goes well, you will see a success message, and you can clone any repository you have access to; in my case, I cloned my own repository.

![Testing ssh key - linux](https://i.imgur.com/eDKiWUy.webp)

### Windows

The same process as Linux except that here I used PowerShell to create the SSH key and Git Bash to test the SSH key.

First, you need to open PowerShell and type the following command:

```powershell
ssh-keygen -t ed25519 -C <your-email>
```

replace `<your-email>` with your GitHub email.

![ssh-keygen on windows](https://i.imgur.com/bCSWptA.webp)

After typing the command, you will be prompted to fill in some information, such as the key name and password. You can type any name as long as you don't forget it; in my case, I just pressed `enter` so that Git would automatically generate the key name and have no password.

With the key generated, you should copy the public key to the clipboard. For this, navigate to the folder where the key was generated (by default it is in the `C:\Users\ryans\.ssh` folder, as shown in the previous image) and type the following command:

```powershell
type id_ed25519.pub
```

and copy the key that appears on the screen.

![getting ssh key in windows](https://i.imgur.com/XdeXkT1.webp)

Finally, now you need to go to the GitHub settings page and add the key you just copied. here a shortcut for you to go directly to the GitHub SSH keys settings page: [SSH Keys Settings Page](https://github.com/settings/keys)

here you should go to `New SSH key` and paste the key you copied earlier.

![paste key on github - windows](https://i.imgur.com/fYitTGb.webp)

By clicking on Add SSH key, you will add the SSH key to GitHub.

Now, just test if the key was added correctly and clone any repository you have access to, always using the SSH address. To test if the key was added correctly, you can type the following command:

```bash
ssh git@github.com
```

if everything goes well, you will see a success message, and you can clone any repository you have access to; in my case, I cloned my own repository.

![Testing ssh key - linux"](https://i.imgur.com/OQaJNyj.webp)

## References

- [Github Documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

I hope this tutorial has helped you set up your SSH key on github. If you have any questions or suggestions, leave a comment below or contact me through [LinkedIn](https://www.linkedin.com/in/ryan25/) or the [contact](https://ryrden.github.io/old-website/contact/) tab on my website.
