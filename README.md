# Advanced-Linux-Commands 

Advanced Linux commands encompass a wide range of tools and techniques used for system administration, network management, and complex data manipulation. These commands often build upon basic commands and offer more granular control and functionality. Examples include grep, sed, awk, find, xargs, systemctl, journalctl, rsync, tmux, and networking tools like ip, ss, nslookup, dig, tcpdump, and iftop. 

## Some key advanced Linux commands: 

1. Text Processing and Manipulation:

- **grep:** A powerful tool for searching text within files or output, using regular expressions for advanced pattern matching. 

- **sed:** Stream editor for performing text transformations like substitutions, deletions, and insertions. 

- **awk:** A versatile language for text processing, allowing you to extract, manipulate, and format data from files. 

- **xargs:** Builds and executes commands from standard input, often used to process lists of files or data. 

- **sort:** Sorts lines of text files. 

- **uniq:** Filters out duplicate lines in a sorted file. 

- **head and tail:** Display the beginning or end of a file, respectively. Useful for quickly inspecting large files. 

- **cat:** Concatenates files and prints them to standard output. Can also be used to create, display, and manipulate files. 

2. File and Directory Management:

- **find:** Recursively searches for files and directories based on various criteria (name, type, modification time, etc.). 

- **chmod:** Changes the permissions of files and directories. 

- **chown:** Changes the ownership of files and directories. 

- **rsync:** Synchronizes files and directories between locations, locally or over a network. 

- **tar:** Creates, extracts, and manipulates archive files (tarballs). 
dd: Used for low-level disk operations, including creating bootable USB drives. 

3. System Information and Monitoring:

- **systemctl:** Controls and manages systemd services. 

- **journalctl:** Queries and displays systemd logs.

- **top:** Displays a dynamic, real-time view of running processes and system resource usage.

- **htop:** An enhanced, interactive process viewer, offering more features than top.

- **iostat:** Reports CPU and I/O statistics. 

- **free:** Displays memory usage information.

- **df:** Reports disk space usage.
lsof: Lists open files and the processes that are using them.

- **uptime:** Shows system uptime and load average.

- **sar:** Collects, reports, and saves system activity information.

- **atop:** Advanced system and process monitoring tool. 

4. Networking:

- **ip:** A modern replacement for ifconfig and route, used to configure and manage network interfaces, routing, and more. 

- **ss:** Displays network connection information, similar to netstat. 

- **netstat:** Displays network connections, routing tables, interface statistics, and more.  

- **nslookup and dig:** Network tools for querying DNS servers and retrieving information about domain names and records. 

- **tcpdump:** Captures network traffic for analysis. 

- **iftop:** Monitors bandwidth usage per interface. 

## File Permissions and Access Rights 

In Linux, managing file permissions and ownership is a vital for controlling who can access, modify, or execute files and directories. Understanding these concepts allows you to maintain the security and integrity of your system. Delving into the key commands and concepts related to file permissions and ownership. 

## Numeric Representation of Permissions 

In Linux, permissions are represents using numeric values. Each permissions **(no permission, read, write, and execute)** is assigned a numeric value: 

- **no permission = 0**  

- **read = 4** 

- **write = 2,** and 

- **execute = 1.** 

These values are combined to represent the permissions for each user class. 

### Permissions Represented by 7

- 4 (read) + 2 (write) + 1 (execute) = 7

- Symbolic: rwx 

- Meaning: Read, write, and execute permission are all granted. 

- Example Context: A script file that the owner needs to read, modify, and execute. 

### Permissions Represented by 5 

- 4 (read) + 1 (execute) = 5

- Symbolic r-x 

- Meaning: Read and execute permissions are granted, but write permission is not. 

- Evample Context: A shared library or a command tool that users can execute and read but not modify. 

### Permission Represented by 6 

- 4 (read) + 2 (write) = 6 

- Symbolic rw- 

- Meaning: Read and write permissions are granted, but execute permission is not. 

- Example Context: A document or a configuration file that the owner needs to read and modify but not execute. 

## Shorthand Representation of Permissions** 

Linux also has a shorthand or symbolic, method for representing file permissions in addition to numeric ways. 

### Understanding User Classes from a Permissions Perspective 

It's important to understand the concepts of "user classes" in the categories of users that Linux recognises when deciding who can do what with a file. There are three main classes. 

- Owner: The person who created the file. Often referred to as 'user'

- Group: A collection of users who shore certain permissions for the file. 

- Others: Anyone else who has access to computer but doesn't fall into the first two categories. 

### The Role of Hyphens (-) in Permission Representation 

In the context of Linux file permissions, a hyphen doesn't actually represent a user class. Instead, it's used in the symbolic representation of permissions to show the absence of a permission. 

Get onto linux terminal and run **ls -latr** 

![Hyphen Role](./img/01.%20Hyphen%20Role.png) 

- In teh output above, it will be notice that some of the first character can **-** 0r **d:** **d** mean it's a directory, **-** means it's a file. 

- The next three characters is **(rwx)** show the permission for the owner, r, w, and x stands for read, write, and execute. 

- If a permission is not granted, **-** will be see in it's place. 

- THe hyphen seperates, owner, group, and others 

- The follwing three charcters after the owner's permissions represents the group's permissions, using the same r, w, and x notation. 

- The last three characters show the permissions for others. 

## File Permission Commands 

To mange file permissions and ownership, Linux provides several commands: 

### chmod command 

The 'chmod' coomand allows you to modify file permissions. you can use both symbolic and numeric representations assign permissions to user, group, and others. 

Lets see an example. 

Create an empty file 

![Create Empty File](./img/02.%20Create%20Empty%20File.png) 

Check the permission of the file. 

![Check Permission](./img/03.%20Check%20Permission.png) 

### The permission of the above output represent

The permission shows that it is file own's by alnuhutecspace since it start with **-**, it can be read and write upon but not granted execute, while the group can also read and write but others can only read. 

Now lets update the permission so that all the user classes will have execute permission. 

![Update Permission](./img/04.%20Update%20Permission.png)

To check for execution of the commands results 

![Check For Permission](./img/05.%20Check%20File%20Permission.png) 

The same command can be executed to achieve the same result using numbers approach. 

![Update Permission with Numbers](./img/06.%20Update%20Permission%20with%20Numbers.png) 

To add execute permissions for all (user, group, others), add 1 to each of the three categories, resulting in 755: 

Imagine the owner of a file is currently the only one with full permission to 'note.txt'. 

![Owner's Full Permission](./img/07.%20Owner's%20Full%20Permission.png)

To allow group members and others to read, write, and execute the file, it to the - rwxrwxrwx permission type, whose numeric value is 777: 

![Groups and Others Full Permission](./img/08.%20Groups%20and%20Others%20Full%20Permission.png) 

Notice the dash "-" in the first position represent the file type and not the user class. 

### chown command 

The chown allows the chnage of ownership files, directories, or symbolic links to a specified username or group. Using the previous user and developer the execution was successfully, but changing the username and developer to new one requires sudo previleges. 

![chown Command](./img/09.%20chown%20Command.png) 

## Superuser Previleges 

It is often necessary to become the superuser to perform important task on linux but should not stay logged in as the superuser. In most linux distributions, there is a command that can give temporary access to the superuser's previleges. This program is called sudo (superuser) and can be used in those cases when the need to be the superuser for a small number of tasks. 

To switch to the root user simply run and type 'exit'. 

![Switch to Root and Exit](./img/10.%20Switch%20to%20Root%20and%20Exit.png) 

## User Management on Linux 

As a DevOps engineer user management in Linux involves creating, modifying, and deleting user accounts, setting permissions, managing groups, and configuring authentication and access controls as a systems administration. 

### Creating a User 

To create a new user on Ubuntu Server, 'adduser' command can be used. Assuming the name of the user to be created is **Joe**. Open the terminal to run this command below. Running the command will prompt for password entering and confirming the password will create new user.  

![Create User](./img/11.%20Create%20User.png)

Once the necessary details are provided the user account will be created, and home directory will be generated automatically for the user. 

![New User Created](./img/12.%20New%20User%20Created.png) 

### Granting Administartion Privileges 

By default, newly created user accounts do not administrative previleges. To grant administartive access to a user, the user can be added to the sudo group. Users with sudo group can run command with administartive priveleges. 

![Grant Admin Previlege](./img/13.%20Grant%20Admin%20User.png) 

- 'usermod:' This is the command that modifies user account. 

- '-aG:' These are flags or parameter used with the usermod command. 

    - -a stands for "append" and is used to add user to the specified group(s) without removing them from other groups they they may already belong to. 

    - -G stands for "supplementary groups" and followed by a comma-seperated list of groups. It specifies the groups to which the user should be added or modified. 

- In the given command, '-aG sudo' is used to add the user 'johndoe' to the **sudo** group. 

- The sudo group is typically associated with administrative or superuser privileges. 

## Task for Me 

- Log out and log back in as the newly created user.  

- Navigate to the '/home/johndoe/ directory to explore what has been created. 

![Task for Me](./img/14.%20Task%20for%20Me.png) 

### Switching User Account 

To switch to another user account, use the 'su' command followed by the username. 

![Switch User Account](./img/15.%20Switch%20User%20Account.png) 

### Modifying User Accounts 

### Changing User Password 

To change the password by a user, the 'passwd' command followed by username should be used.

![Change User Password](./img/16.%20Change%20User%20Password.png) 

## Task 2 for Me

Test the updated password by logging on the server, using the newly created password. 

![Task 2 for Me](./img/17.%20Task%202%20for%20Me.png) 

When exited after the update of the new password the server switch back to original user, login back to the new user account paasword was prompted and the newly created was use. 

### Creating Group 

To create new group, use the 'groupadd' command. 

![Create Group](./img/18.%20Create%20Group.png) 

### Adding Users to the Group 

Use the 'usermod' command to add users to the group. For example, to add users "john" and "jane" to the "developer" group: 

User 'john' was created to be added to developer group, same can be use for any newly created user. 

![User John Created](./img/19.%20User%20John%20Created.png)

Now to add the user "john" to developers group we use. 

![Adding User to Group](./img/20.%20Adding%20User%20to%20Group.png)

### Verifying Group Membership 

To confirm the group memberships for a specfic user, use 'id' command. 

![Verifying Group Membership](./img/21.%20Verifying%20Group%20Membership.png) 

### Deleting a User 

To delete a user run the command below

![Deleting User](./img/23.%20Deleting%20User.png) 

### Ensuring Proper Group Permissions 

Groups in Linux are often used to manage permissions for files and directories. Ensure that the relevant files or directories have the appropriate group ownership and permissions. 

## Side Hustle Task 

- Create a group on the server and name it 'devops'. 

![DevOps Group](./img/24.%20DevOps%20Group.png) 

- Create 5 users '["mary""mohammed""ravi""tunji""sofia"]', and ensure each user belong to devops group. It's done as shown the previous commands. 

![Adding User to Group](./img/25%20Adding%20Users%20to%20Group.png)

- create a folder for each user in '/home' directory for example '/home/mary'. 

- Ensure that the group ownership of each created folder belongs to **devops**

![Group Ownership of Folder](./img/26.%20Group%20Ownership%20of%20Folder.png)