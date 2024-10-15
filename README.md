# On-Premises MySQL Database Migration to Google Cloud

This project provides a step-by-step guide to configure a Google Cloud VM and migrate an on-premises MySQL database to the cloud.

## Table of Contents
- VM Configuration
- MySQL Installation and Configuration
- Database Connectivity
- Database Migration and Backup
- Cloud SQL Integration



## VM Configuration
The Google Cloud VM is configured with the following specifications:
- **Zone**: `us-west1-a`
- **Machine Type**: `E2-medium` (2 vCPUs, 4 GB RAM)
- **Storage**: 10 GB persistent disk
- **Firewall Configuration**: Allows HTTP, HTTPS, and MySQL (port 3306) traffic.

## MySQL Installation and Configuration
1. **Install MySQL**:
   - Install MySQL on the VM using the appropriate package manager for the operating system.
2. **Configure MySQL for Remote Access**:
   - Modify the `bind-address` to `0.0.0.0` in the MySQL configuration file to allow remote connections.
3. **Static IP Assignment**:
   - Reserve a static IP for consistent connectivity to the VM.

## Database Connectivity
Connect to the MySQL instance on the VM using MySQL Workbench:
1. Install MySQL Workbench on the on-premises machine.
2. Open a new connection profile in MySQL Workbench.
3. Set the hostname and port to the VM’s external IP and port 3306.
4. Use the configured username and password to connect.

## Database Migration and Backup
1. **Backup Existing Database**:
   - Use `mysqldump` to create a backup of the database.
   - Transfer the backup to the VM using `scp`.
2. **Restore Database on Cloud VM**:
   - Import the backup SQL file into the MySQL instance on the VM.
3. **SSH Key and PowerShell Connection**:
   - Generate an SSH key and connect to the VM using PowerShell for direct access.

## Cloud SQL Integration
To integrate with Cloud SQL:
1. Create connection profiles for both the VM MySQL server and the Cloud SQL instance.
2. Configure a migration job and set up a Cloud SQL instance as a read replica.
3. Add the Cloud SQL outgoing IP to the VM MySQL settings to allow access.

## Project Overview Diagram
![Project Overview](https://github.com/J0vial/Google-cloud-Migration/blob/main/project.png)

By following this guide, you can successfully migrate an on-premises MySQL database to a Google Cloud instance.
