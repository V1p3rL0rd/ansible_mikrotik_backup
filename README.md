# Ansible Mikrotik Backup

Ansible project for automatic backup of Mikrotik routers configuration.

## Project Structure

```
.
├── backups/                    # Directory for storing backups
├── group_vars/                 # Group variables
│   └── mikrotik/              
│       └── vars.yml           # Variables for mikrotik group
├── roles/                      # Roles
│   └── mikrotik_backup/       # Role for creating backups
├── inventory.ini              # Inventory file
└── site.yml                   # Main playbook
```

## Requirements

- Ansible 2.9+
- sshpass

## Setup

1. Edit the `inventory.ini` file by adding your routers' IP addresses
2. Configure credentials in `group_vars/mikrotik/vars.yml`
3. If needed, modify the backup path in `roles/mikrotik_backup/defaults/main.yml`

## Usage

```bash
ansible-playbook site.yml
```

## Security

It is recommended to store passwords in encrypted form using Ansible Vault:

```bash
ansible-vault encrypt group_vars/mikrotik/vars.yml
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.
