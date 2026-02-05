# Day 11 Challenge

## Files & Directories Created
- devops-file.txt  
- team-notes.txt  
- project-config.yaml  
- app-logs/  
- heist-project/  
- bank-heist/

## Ownership Changes

- devops-file.txt : user → tokyo → berlin
- team-notes.txt : group → heist-team  
- project-config.yaml : professor:heist-team  
- app-logs : berlin:heist-team  
- heist-project/* : professor:planners  

- access-codes.txt → tokyo:vault-team
- blueprints.pdf → berlin:tech-team
- escape-plan.txt → nairobi:vault-team

## Commands Used
```
sudo chown tokyo devops-file.txt
sudo chown berlin devops-file.txt
sudo chgrp heist-team team-notes.txt
sudo chown professor:heist-team project-config.yaml
sudo chown berlin:heist-team app-logs
sudo chown -R professor:planners heist-project/
sudo chown tokyo:vault-team bank-heist/access-codes.txt
sudo chown berlin:tech-team bank-heist/blueprints.pdf
sudo chown nairobi:vault-team bank-heist/escape-plan.txt

```


## What I Learned

1. Ownership defines who can control a file and directory
2. chown can be used to change group and owner together instead of doing seperately with chgrp and chown
3. -R helps to change owner and group of files which are under a directory
