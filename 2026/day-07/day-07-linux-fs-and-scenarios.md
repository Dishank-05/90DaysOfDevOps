Linux File System Hierarchy

/ :- It is the starting point of file system also known as root directory

/home :- It is home directory of linux file system and all users directory are present over here             and I will use this directory to store scripts and specific user files

/root :- It is root's user home directory seperate from /home and I will use this when i am working          as root user.

/etc :- /etc is a directory which has all configuration files of services and applications like 
         passwd and hosts file . I will use this when modifying system or sys configs
    
/var/log :- All system services and application logs would be present on this path , I will
            use this when troubleshooting with service failures to view logs

/tmp :- Temporary directory used by application to store temporary data , I will use this for 
        storing temporary data

/bin :- Contains system binaries/command which are needed while system boot I will use this for 
        running simple Linux Commands

/usr/bin :- This directory has all the user installed commands which can be executed on daily basis             like git, python

/opt :- It is used for third party software installation and I will use this when i want to run any         application manually

================================================================================================

Hands On Command

================================================================================================

du -sh /var/log/* 2>/dev/null | sort -h | tail -5 : Helps Identify which log file has most size.

cat /etc/hostname : Shows hostname of system

ls -la ~ : Shows all files including hidden files as well present in home directory of user

==============================================================================================

Scenario based 

==============================================================================================


Application server is slow and we need to find which process is consuming high CPU.

Step 1: top
Why : Shows all real time CPU and memory usage which will help me to identify process at top which is using high CPU

Step 2: ps aux --sort=-%cpu | head -10
Why : Shows top 10 process consuming high CPU in ascending order

Step 3: ps -o pid,pcpu,pmem,comm -p PID
Why : Check exact CPU and memory usage of that process


Finding Service Logs

Step 1 : systemctl status docker
Why : To check whether docker service is active , failed or stopped

Step 2 : journalctl -u docker -n 50
Why : TO check latest 50 logs of docker service

Step 3 : journalctl -u docker -f
Why : To monitor live logs of docker service



File Permission Issue

Step 1: ls -l /home/user/backup.sh
Why: To check for current permission of that file whether it has execute permission or not

Step 2: chmod +x /home/user/backup.sh
Why: If permission is not there , this command will make file executable

Step 3: ls -l /home/user/backup.sh
Why : To make sure that the required executable permission is being applied on file

Step 4: ./backup.sh
Why : To run the file 
