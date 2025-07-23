Ansible Mikrotik Backup 💾

This Ansible playbook provides a simple way to automate backups of your Mikrotik router configurations. It connects to your Mikrotik devices, exports their configuration, and saves it to a local backups directory with a timestamp and the router's identity in the filename.

Features ✨
Automated Backups: Easily back up your Mikrotik router configurations.

Timestamped Files: Each backup is saved with a unique timestamp for easy versioning.

Router Identity: Backups are named using the router's system identity (or hostname if identity isn't available).

SSH Support: Connects to Mikrotik devices over SSH, supporting both password-based authentication (via sshpass) or key-based authentication.

Local Storage: Backups are stored in a dedicated backups directory on your Ansible control machine.

Requirements 🛠️
Before running this playbook, make sure you have the following:

Ansible: Installed on your control machine.

sshpass: If you plan to use password-based authentication for your Mikrotik routers (as in the example inventory), sshpass must be installed on your Ansible control machine.

On Debian/Ubuntu: sudo apt-get install sshpass

On RedHat/CentOS: sudo yum install sshpass

SSH Access: Your Ansible control machine must have SSH access to your Mikrotik routers.

Getting Started 🚀
1. Clone the Repository (or create the files)
Clone your repository:

Bash

git clone https://github.com/V1p3rL0rd/ansible_mikrotik_backup.git
cd ansible_mikrotik_backup


2. Replace examples to your mikrotik routers in inventory.ini file

Ini, TOML

[mikrotik]
10.100.242.2 ansible_user=admin ansible_ssh_pass='Str0ngPa$$w0rd123!' ansible_port=22 #Office01
10.100.242.4 ansible_user=admin ansible_ssh_pass='Str0ngPa$$w0rd123!' ansible_port=22 #Office02
10.100.242.6 ansible_user=admin ansible_ssh_pass='Str0ngPa$$w0rd123!' ansible_port=22 #Office03
10.100.242.8 ansible_user=admin ansible_ssh_pass='Str0ngPa$$w0rd123!' ansible_port=22 #Office04


3. Run the Playbook 🏃
Execute the playbook from your terminal:

Bash

ansible-playbook -i inventory.ini mt-backup.yml
How it Works ⚙️
Ensure backup directory exists: Creates a backups directory in the playbook's execution location on your Ansible control machine if it doesn't already exist.

Set ssh port: Ensures the ansible_port variable is set, defaulting to 22 if not explicitly defined.

Get current timestamp: Fetches the current date and time to be used in the backup filename.

Get router identity: Connects to the Mikrotik router and retrieves its system identity (/system identity print). This is used for a more descriptive backup filename. If identity cannot be retrieved, the hostname from inventory will be used.

Process router identity: Cleans up the router identity string to create a valid filename.

Perform router backup: Connects to the Mikrotik router and runs the /export command, which outputs the router's full configuration.

Debug variables for verification: (Optional) Shows the intended backup filename and other details for verification during playbook execution.

Save backup to file: Saves the exported configuration content to a .rsc file within the backups directory, using the router's processed identity and the timestamp in the filename (e.g., backups/MyRouter_2024-07-23_10-00-00.rsc).

Contributing 🤝
Feel free to open issues or submit pull requests if you have improvements or find bugs!
