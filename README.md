# ft_linux - How to Train Your Kernel

![Wallpaper](wallpaper.jpg)

## Summary

This project involves building a basic but functional Linux distribution as the foundation for future kernel projects. The distribution will include a custom-built Linux kernel, specific binaries, a compliant filesystem hierarchy, and internet connectivity.

## Table of Contents

- [Introduction](#introduction)
- [Goals](#goals)
- [General Instructions](#general-instructions)
- [Mandatory Part](#mandatory-part)
- [Bonus Part](#bonus-part)

## Introduction

Welcome to **ft_linux**! In this project, the goal is to create a Linux distribution that serves as the base for kernel projects. The distribution should be a functional environment where kernel code is executed.

## Goals

- Build a Linux Kernel.
- Install specific binaries (refer to the [Packages to Install](#mandatory-part) section).
- Implement a filesystem hierarchy compliant with standards.
- Connect to the Internet.

## General Instructions

### Virtual Machine

- Use VirtualBox or VMWare for development.

### Read Standards

- While not required, reading certain standards is recommended.

### Kernel Version

- Use a kernel version >= 4.0.

### Kernel Sources

- Place kernel sources in `/usr/src/kernel-$(version)`.

### Partitions

- Use at least 3 different partitions (root, /boot, and a swap partition).

### Kernel Module Loader

- Implement a kernel module loader like udev.

### Kernel Version in Hostname

- Include your student login in the kernel version (e.g., 'Linux kernel 4.1.2-<student_login>').

### Distribution Hostname

- Set the distribution hostname to your student login.

### System Architecture

- Choose between a 32-bit or 64-bit system.

### Management and Configuration Software

- Use SysV or SystemD for central management and configuration.

### Bootloader

- Ensure your distro boots with a bootloader (LILO or GRUB).

### Kernel Binary Naming

- Name the kernel binary in /boot as `vmlinuz-<linux_version>-<student_login>`.

## Mandatory Part

### Packages to Install

- Install the specified packages or their equivalents. Versions are provided, but you are free to choose.

[List of packages...]

## Bonus Part

### System Stability Check

- Ensure the mandatory part is perfect before proceeding to the bonus part.

### System Customization

- Install additional software, GUI, or any preferred components.

### X Server and Window Managers

- Earn extra points for installing an X Server and window managers/desktop environments (e.g., GNOME, LXDE, KDE, i3, dwm)
- ## Bonus Part

### System Stability Check

Ensure the mandatory part is perfect before proceeding to the bonus part.

### System Customization

Install additional software, GUI, or any preferred components.

### X Server and Window Managers/Desktop Environments

Earn extra points for installing an X Server and window managers/desktop environments. Choose one or more from the options below:

- **X Server:**
  - Install an X Server to provide the graphical foundation for your desktop environment.
  
  **Window Managers/Desktop Environments:**
  - Choose and install one or more of the following:
    - GNOME
    - LXDE
    - KDE
    - i3
    - dwm
    - [Add any other window manager or desktop environment you prefer]

Ensure that the X Server and your chosen window manager/desktop environment are properly configured and functional.

EOF

# Tasks:

## linux version:
`git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git;
cd linux;
git checkout v4.0 (or higher)`

## installing specific Binaries:
`sudo apt update;
sudo apt install <package-name>`

## Implementing a filesystem hierarchy in Linux 
`mkdir -p /{bin,boot,dev,etc,home,lib,media,mnt,opt,proc,root,run,sbin,srv,sys,tmp,usr,var}
chmod 755 /{bin,boot,dev,etc,home,lib,media,mnt,opt,proc,root,run,sbin,srv,sys,tmp,usr,var}`

## Configure your network settings in a virtual machine

Set the Network Adapter: In your virtual machine settings, go to the "Network" tab. Here, you can set the network adapter to either NAT (Network Address Translation) or Bridged Adapter. NAT allows your virtual machine to share the host's IP address, while Bridged Adapter makes the virtual machine appear as another device on the same network as the host.
Configure the Network Interface: Once the network adapter is set, you need to configure the network interface within your Linux distribution. This usually involves editing the network configuration files located in /etc/network/interfaces or /etc/netplan/ (depending on your distribution).
Here's an example of how you might set up a static IP address using Netplan (for newer versions of Ubuntu):



network:
 version: 2
 renderer: networkd
 ethernets:
   enp0s3:
     dhcp4: no
     addresses: [192.168.1.10/24]
     gateway4: 192.168.1.1
     nameservers:
       addresses: [8.8.8.8, 8.8.4.4]

EOF
`
sudo systemctl restart networking
`
