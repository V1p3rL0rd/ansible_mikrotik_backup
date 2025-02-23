# Ansible mikrotik router backup
This simple Ansible playbook automates the process of creating backups of Mikrotik routers.

The script is executed in several stages:

1) Ensure local backup directory exists
2) Get device identity
3) Extract device identity
4) Create backup on Mikrotik device
5) Fetch backup file from Mikrotik device to local directory "~/.backups"
6) Debug backup creation status
7) Debug backup fetch status
