# samba-ftp-fileserver
Configuring a Linux file server with Samba and FTP for corporate departments
# Linux File Server Project: Samba & FTP Implementation

This repository contains the configuration and setup guide for a Linux-based file server designed for a corporate network environment. The goal was to implement a secure, scalable, and department-isolated storage system.

## 🛠 Features & Capabilities
- Cross-Platform Sharing: Fully compatible with Windows (SMB/CIFS) and Linux clients.
- Role-Based Access Control (RBAC): Access managed via system groups (`smbgroup`).
- Private Share: Restricted access to authorized personnel (Permissions: `770`).
- Public Share: A common exchange area for all users (Permissions: `777`).
- Network Services: Integrated with isc-dhcp-server for local IP management.

## 📂 Share Structure
| Share Name | Physical Path | Access Level | Target Audience |
| :--- | :--- | :--- | :--- |
| public | /samba/public | Guest Allowed | All Employees |
| private | /samba/private | Authorized Only | IT 

## 🚀 Quick Setup Guide

### 1. Group & User Provisioning
```bash
sudo groupadd smbgroup
sudo usermod -aG smbgroup <username>
sudo smbpasswd -a <username>
sudo chown -R root:smbgroup /samba/private
sudo chmod -R 770 /samba/private
sudo chown -R root:smbgroup /samba/private
sudo chmod -R 770 /samba/private
sudo systemctl restart smbd
