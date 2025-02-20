This playbook is a simple script for automating backups on Mikrotik routers.

The script is executed in several stages:

1) Connection to the mikrotik host group with the specified login and password.

2) Checking the existence of a local directory for downloading backups and creating it if necessary.

3) Get the device identity.

4) Creating a backup on each router with the name of the device and the date of creation.

5) Copying the created backups to the local host in the specified directory.

6) Displaying the status of creating a backup and uploading the backup file to the local host.
