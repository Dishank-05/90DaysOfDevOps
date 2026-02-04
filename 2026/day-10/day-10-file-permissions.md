# Day 10 Challenge

## Files Created

[devops.txt , notes.txt , project , script.sh]

## Permission Changes

###Before permission changes 
'''
-rw-r--r--. 1 ec2-user ec2-user  0 Feb  3 14:45 devops.txt
-rw-r--r--. 1 ec2-user ec2-user 27 Feb  3 14:48 notes.txt
-rw-r--r--. 1 ec2-user ec2-user 24 Feb  3 14:56 script.sh
'''

###After permission changes
'''
-r--r--r--. 1 ec2-user ec2-user  0 Feb  3 14:45 devops.txt
-rw-r-----. 1 ec2-user ec2-user 27 Feb  3 14:48 notes.txt
drwxr-xr-x. 2 ec2-user ec2-user  6 Feb  3 15:07 project
-rw-r--r--. 1 ec2-user ec2-user 24 Feb  3 14:56 script.sh
'''

## Commands Used
'''
touch devops.txt
echo "Adding a line in notes.txt" >notes.txt
vim script.sh
cat notes.txt
head -n 5 /etc/passwd
tail -n 5 /etc/passwd
chmod 755 script.sh
chmod 444 devops.txt
chmod 640 notes.txt
mkdir project
chmod 755 project/
cat "Another line" >devops.txt
chmod a-x script.sh
ls -l
./script.sh
'''

## What I Learned
1. Permissions play a critical role in controlling read, write, and execute access for users and groups.
2. A script cannot be executed without execute (x) permission, and it results in “Permission denied”.
3. Linux file permissions help secure files from accidental modification or unauthorized access.
