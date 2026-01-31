Quick run and checks for a Linux System

1. Environment Checks
    uname -a : Gives System related information 
    cat /etc/os-release : Retrieves OS related info ,version info and ID info

2. FileSystek Checks
    mkdir /tmp/runbook-demo : Create runbook-demo directory inside tmp directory
    cp /etc/hosts /tmp/runbook-demo/hosts-copy : copies all host entries to host-copy file
    ls -l /tmp/runbook-demo : List all files inside runbook-demo

    This specific checks ensures that everything is proper with filesystem checks if there is disk      space issue or permission issue this can lead to failure of anykind of systemd services

3.  Memory & CPU Checks
     top : Shows real time CPU and memory usage of all process
     free -h : Displays total,used and available RAM
     ps -o pid,pcpu,pmem,comm -p PID : Gives CPU and memory usage of a specific process

4.  Disk & IO checks
     df -h : Shows Disk usage
     du -sh /var/log : Check size of log directory

5.  Network Checks
     ss -tulpn : Gives open ports and listening services
     curl -I endpoint : Checks service reachability

6. Log checks
    tail -n 50 /var/log/file.log : Checks latest 50 logs of given file
    journalctl -u docker -n 50 : Shows last 50 logs of docker service

If something gets worse

1. First check logs of service which has issue if its configuration level issue then change configuration and restart service
2. Check if disk is full and if its full try to clean old logs since service can't write logs if no space is left 
3. Check which process is utilising more CPU and try to stop or optimize services which are not of any use

