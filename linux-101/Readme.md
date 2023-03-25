# Overview
Welcome to our linux-101 docs! We've created a comprehensive list of topics to help you master the essential concepts and commands for working with Linux operating systems. Each topic includes a set of lab exercises designed to give you practical, hands-on experience with the material. Our goal is to help you gain a thorough understanding of Linux and feel confident working with it in a professional setting. We hope you find this repository helpful and informative!

## File System
In this section, you will learn about the Linux file system and the commands used to manipulate files and directories.

### Exercise 1
1. Create a new directory named my_directory.
2. Navigate into my_directory.
3. Create a new file named my_file.txt.
4. Add some text to my_file.txt.
5. Rename my_file.txt to my_new_file.txt.
6. Move my_new_file.txt to the parent directory.
7. Remove the my_directory directory.


<details>
<summary>Solution:</summary>

    mkdir my_directory
    cd my_directory
    touch my_file.txt
    echo "This is my file." > my_file.txt
    mv my_file.txt my_new_file.txt
    mv my_new_file.txt ..
    cd ..
    rm -r my_directory

</details>

### Exercise 2
1. Create a new directory named backup.
2. Copy the file /etc/passwd to the backup directory.
3. Compress the backup directory into a tar  archive.
4. Extract the tar archive to a new directory named restored.
5. Check the contents of the restored directory to ensure that the file was restored correctly.
<details>
<summary>Solution:</summary>

    mkdir backup
    cp /etc/passwd backup/
    tar -czf backup.tar.gz backup/
    mkdir restored
    tar -xzf backup.tar.gz -C restored/
    ls restored/

</details>

## Disk Partitioning
In this section, you will learn about disk partitioning and how to manage disk partitions using the fdisk and parted commands.

### Exercise 1
1. List the current partitions on your system.
2. Create a new partition using fdisk.
3. Create a new file system on the partition using mkfs.
4. Mount the partition to a new directory named my_mount_point.
5. Add a new entry to /etc/fstab so that the partition is mounted automatically at boot time.

<details>
<summary>Solution:</summary>

    # List the current partitions
    sudo fdisk -l

    # Create a new partition
    sudo fdisk /dev/sda
    # Enter n to create a new partition
    # Choose the default partition number, starting sector, and ending sector
    # Enter w to write the changes and exit

    # Create a new file system
    sudo mkfs.ext4 /dev/sda3 #change 3 to your partition number in this command and rest of the commands

    # Mount the partition
    sudo mkdir /mnt/my_mount_point
    sudo mount /dev/sda3 /mnt/my_mount_point

    # Add an entry to /etc/fstab
    echo '/dev/sda3 /mnt/my_mount_point ext4 defaults 0 0' | sudo tee -a /etc/fstab

</details>

### Exercise 2
Resize an existing partition using parted.
1. Create a new partition using the free space created by resizing the existing partition.
2. Create a new file system on the new partition using mkfs.
3. Mount the new partition to a new directory named my_new_mount_point.
Add a new entry to /etc/fstab so that the partition is mounted automatically at boot time.

<details>
<summary>Solution:</summary>

    # Resize an existing partition
    sudo parted /dev/sda
    # Enter print to list the existing partitions
    # Enter resizepart <partition number> <end>
    # Enter print to verify that the partition was resized
    # Enter quit to exit

    # Create a new partition
    sudo parted /dev/sda
    # Enter mkpart
    # Choose the default partition type, file system, start, and end
    # Enter quit to exit
    # Create a new file system
    sudo mkfs.ext4 /dev/sda4

    # Mount the new partition
    sudo mkdir /mnt/my_new_mount_point
    sudo mount /dev/sda4 /mnt/my_new_mount_point

    # Add an entry to /etc/fstab
    echo '/dev/sda4 /mnt/my_new_mount_point ext4 defaults 0 0' | sudo tee -a /etc/fstab
</details>

## Users and Groups
In this section, you will learn how to manage users and groups on a Linux system.

### Exercise 1
1. Create a new user named my_user.
2. Set a password for the new user.
3. Add the new user to the sudo group.
4. Check that the new user can run commands with sudo.
5. Delete the new user.

<details>
<summary>Solution:</summary>

    # Create a new user
    sudo adduser my_user

    # Set a password for the new user
    sudo passwd my_user

    # Add the new user to the sudo group
    sudo usermod -aG sudo my_user

    # Check that the new user can run commands with sudo
    su - my_user
    sudo ls
    exit

    # Delete the new user
    sudo deluser my_user

</details>

### Exercise 2
1. Create a new group named my_group.
2. Add a user to the new group.
3. Check the group membership of the user.
4. Create a new file and set the group ownership to my_group.
5. Check the group ownership of the file.
6. Change the group ownership of the file to sudo.
7. Delete the new group.

<details>
<summary>Solution:</summary>

    # Create a new group
    sudo groupadd my_group

    # Add a user to the new group
    sudo usermod -aG my_group my_user

    # Check the group membership of the user
    groups my_user

    # Create a new file and set the group ownership to my_group
    touch my_file.txt
    sudo chgrp my_group my_file.txt

    # Check the group ownership of the file
    ls -l my_file.txt

    # Change the group ownership of the file to sudo
    sudo chgrp sudo my_file.txt

    # Delete the new group
    sudo groupdel my_group

</details>

## File Permissions
In this section, you will learn about file permissions and how to manage them using the chmod and chown commands.

### Exercise 1

1. Create a new file named my_file.txt.
2. Set the permissions of the file to rw-r--r--.
3. Check the permissions of the file using ls -l.
4. Change the owner of the file to my_user.
5. Check the owner of the file using ls -l.
Delete the file.

<details>
<summary>Solution:</summary>

    # Create a new file
    touch my_file.txt

    # Set the permissions of the file
    chmod 644 my_file.txt

    # Check the permissions of the file
    ls -l my_file.txt

    # Change the owner of the file
    sudo chown my_user my_file.txt

    # Check the owner of the file
    ls -l my_file.txt

    # Delete the file
    rm my_file.txt

</details>

### Exercise 2
1. Create a new directory named my_directory.
2. Set the permissions of the directory to rwxr-xr-x.
3. Check the permissions of the directory using `ls -ld`.
4. Create a new file inside the directory.
5. Check the permissions of the new file using `ls -la`

<details>
<summary>Solution:</summary>

    # Create a new directory
    mkdir my_directory

    # Set the permissions of the directory
    chmod 755 my_directory

    # Check the permissions of the directory
    ls -ld my_directory

    # Create a new file inside the directory
    touch my_directory/my_file.txt

    # Check the permissions of the new file
    ls -l my_directory/my_file.txt

</details>

## Package Management
In this section, you will learn how to manage packages on a Linux system using the apt package manager.

### Exercise 1
1. Update the package index.
2. Install the nginx package.
3. Start the nginx service.
4. Check the status of the nginx service.
5. Stop the nginx service.
6. Remove the nginx package.

<details>
<summary>Solution:</summary>

    # Update the package index
    sudo apt update

    # Install the nginx package
    sudo apt install nginx

    # Start the nginx service
    sudo systemctl start nginx

    # Check the status of the nginx service
    sudo systemctl status nginx

    # Stop the nginx service
    sudo systemctl stop nginx

    # Remove the nginx package
    sudo apt remove nginx

</details>

### Exercise 2
1. List all installed packages.
2. Search for the package that provides the ifconfig command.
3. Install the package that provides the ifconfig command.
4. Check that the ifconfig command is now available.
5. Remove the package that provides the ifconfig command.

<details>
<summary>Solution:</summary>

    # List all installed packages
    sudo apt list --installed

    # Search for the package that provides the ifconfig command
    sudo apt search ifconfig

    # Install the package that provides the ifconfig command
    sudo apt install net-tools

    # Check that the ifconfig command is now available
    ifconfig

    # Remove the package that provides the ifconfig command
    sudo apt remove net-tools
</details>

## Networking
In this section, you will learn how to manage networking on a Linux system using the ip command.

### Exercise 1
1. List all network interfaces.
2. Check the IP address of the eth0 interface.
3. Change the IP address of the eth0 interface to 192.168.1.100/24.
4. Check the IP address of the eth0 interface again.

<details>
<summary>Solution:</summary>

    # List all network interfaces
    ip link show

    # Check the IP address of the eth0 interface
    ip addr show eth0

    # Change the IP address of the eth0 interface
    sudo ip addr add 192.168.1.100/24 dev eth0

    # Check the IP address of the eth0 interface again
    ip addr show eth0

</details>

### Exercise 2
1. Check the default gateway.
2. Add a new default gateway with the IP address 192.168.1.1.
3. Check the default gateway again.
4. Remove the new default gateway.

<details>
<summary>Solution:</summary>

    # Check the default gateway
    ip route show default

    # Add a new default gateway
    sudo ip route add default via 192.168.1.1

    # Check the default gateway again
    ip route show default

    # Remove the new default gateway
    sudo ip route del default via 192.168.1.1

</details>

## Remote Access using SSH
In this section, you will learn how to connect to a remote Linux system using SSH.

### Exercise 1
You will need another VM to do this exercise.
1. Connect to a remote Linux system with the IP address 192.168.1.2.
2. Check the hostname of the remote system.

<details>
<summary>Solution:</summary>

    # Connect to a remote Linux system with the IP address 192.168.1.2
    ssh user@192.168.1.2

    # Check the hostname of the remote system
    hostname
</details>

### Exercise 2
1. Create a new SSH key pair on your local system.
2. Copy the public key to the remote system.
3. Connect to the remote system using the SSH key pair.

<details>
<summary>Solution:</summary>

    # Create a new SSH key pair on your local system
    ssh-keygen -t rsa -b 4096

    # Copy the public key to the remote system
    ssh-copy-id user@192.168.1.2

    # Connect to the remote system using the SSH key pair
    ssh user@192.168.1.2

</details>

### Exercise 3
1. Configure SSH to use a custom port for connections.
2. Connect to the remote system using the custom port.

<details>
<summary>Solution:</summary>

    # Configure SSH to use a custom port for connections
    sudo nano /etc/ssh/sshd_config
    # Edit the "Port" line to use a custom port number (e.g. 2222)
    sudo systemctl restart sshd

    # Connect to the remote system using the custom port
    ssh -p 2222 user@192.168.1.2

</details>

## Logging and Troubleshooting

In this section, you will learn how to troubleshoot issues in Linux and use system logs to find information.

### Exercise 1
1. Check the system logs for errors.
2. Identify the cause of the error.

<details>
<summary>Solution:</summary>

    # Check the system logs for errors
    sudo cat /var/log/syslog | grep error

    # Identify the cause of the error
    # Look for any error messages and investigate the cause based on the message

</details>

### Exercise 2
1. Check the status of a service.
2. Restart the service if it is not running.

<details>
<summary>Solution:</summary>

    # Check the status of a service
    systemctl status apache2

    # Restart the service if it is not running
    sudo systemctl restart apache2

</details>

### Exercise 3
1. Identify the user who last logged into the system.
2. Check the user's activity.

<details>
<summary>Solution:</summary>

    # Identify the user who last logged into the system
    last

    # Check the user's activity
    # Look for any suspicious activity (e.g. unauthorized access attempts, commands that the user shouldn't be running, etc.)

</details>