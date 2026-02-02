# Day 09 Challenge

## Users & Groups Created
- Users: tokyo, berlin, professor, nairobi
- Groups: developers, admins, project-team

## Group Assignments
[ tokyo : tokyo developers project-team , berlin : berlin developers admins , professor : professor admins , nairobi : nairobi project-team  ]

## Directories Created
[ drwxrwxr-x. 2 root developers   51 Feb  2 16:06 dev-project
drwxrwxr-x. 2 root project-team 25 Feb  2 16:25 team-workspace ]

## Commands Used
[ useradd -m : to create user with home directoy
  groupadd : to create group 
  usermod -aG : To add user to a specific group
  chgrp : To change group permission of directoty/files
  chmod : To change rwx permission of directory/files
  sudo -u : To run command with specific use
]

Learned Linux user & group management – creating users, mapping them to groups, modifying folder permissions, and testing access by creating files with different users in shared directories.
I came to know that file and folder permission are necessary if you want to access file via specific user
Before Executing file always check the file permission 
