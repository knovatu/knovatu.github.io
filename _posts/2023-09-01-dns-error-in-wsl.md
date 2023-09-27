---
title: DNS error in Windows Subsystem Linux (WSL)
date: 2023-09-01 22:00:00 -0300
categories: [Tutorials, Windows]
tags: [wsl, dns, windows]
mermaid: true
---

Some time ago I decided to update the Operating System of my laptop (Windows 10), and I chose to do a clean installation of Windows 11 to avoid conflicts with the configs of the previous version of Windows. With the OS installation complete, I started installing the essential tools I always use on Linux, in this case, using Windows Subsystem Linux (WSL 2) running Ubuntu 20.04 with no desktop environment.

I started by updating my distribution, but when I tried to do so, I got an error that seemed like I had no internet access, i.e. it couldn't resolve any URLs from Ubuntu. If you find yourself in the same situation, the problem may be your DNS. When you install Ubuntu via WSL, a local IP address is set as your DNS in your settings, which is why you don't have an internet connection. One possible solution would be to use Google's DNS, which I explain below.

## Fixing this problem

In the first place, try deleting the `resolv.conf` and `wsl.conf` files located in the `/etc` folder.

```sh
sudo rm -f /etc/resolv.conf /etc/wsl.conf
```
{: .nolineno }

Some times, it is not possible to execute that command with `sudo` privileges, so do it from the Root user. In this case, you need to have the user enabled and then access using the `su` command. If the `wsl.conf` file doesn't exist, no problem, remove the `/etc/wsl.conf` parameter from the command line shown above and run it normally.

Once the files have been successfully removed, recreate the `resolv.conf` file with Google's DNS using the following command:

```sh
sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf
```
{: .nolineno }

Next, run the following command to recreate the `wsl.conf` file in the `/etc` folder with those configurations.

```sh
sudo echo -e "[network]\ngenerateResolvConf = false" > /etc/wsl.conf
```
{: .nolineno }

### Shutdown WSL

Finally, for all the changes to be applied correctly, close WSL from Windows PowerShell with the following command:

```sh
# Option-1
wsl --terminate <distroName>

# Option-2
wsl --shutdown
```
{: .nolineno }

### Start WSL

When Ubuntu starts, you should have an Internet connection, and you could be able to install everything you need. Start WSL with the following command:

```sh
wsl -d <distroName>
```
{: .nolineno }
