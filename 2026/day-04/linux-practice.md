ps -ef | grep docker : To check process of docker is running or not
pgrep docker : Retrieves PID of docker
systemctl status docker : Checks whether docker is running or not in background
systemctl list-units --type=service --state=running : Retrieves information of services which are currently active
journalctl -u docker : Retrieves logs of docker service
