### CheatSheet Refresh
Top 5 commands I'll use if incident occurs:
1. top - Give live CPU/Memory utilisation by process
2. ps aux - Snapshot of all running process
3. journalctl -u <service> -n 50 : Shows latest log of service
4. systemctl status <service> :- Checks whether a service is active or not
5. free -h : Shows Available and Used Memory of system
6. df -h : To check disk usage of system

### Commands Revisited
- systemctl status nginx – checked service health
- journalctl -u nginx – viewed service logs
- ps aux | grep nginx – verified running process
- chmod 750 notes.txt – permission practice
- chown root:tech-team notes.txt – ownership change

### 2. How to check service health?
- systemctl status nginx
- journalctl -u nginx
- ps aux | grep nginx

### 3. Safe ownership change example
sudo chown user:group filename

### 4. Focus next 3 days
- Learning how to analyze which process using most CPU and memory
- Building strong fundamental on networking concepts
- Learning basic of shell scripting
