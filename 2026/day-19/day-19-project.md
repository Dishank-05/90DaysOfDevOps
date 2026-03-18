# Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab


### Task 1: Log Rotation Script

```bash
#!/bin/bash

LOG_DIR=$1

if [ -z "$LOG_DIR" ]; then
       echo "Usage: $0 <log_directory>"
       exit 1
fi

if [ ! -d "$LOG_DIR" ]; then
        echo "Directory doesn't exist"
        exit 1
fi

compressed=0
deleted=0

for file in $(find "$LOG_DIR" -name "*.log" -mtime +7); do
        gzip "$file"
        ((compressed++))
done

for file in $(find "$LOG_DIR" -name "*.gz" -mtime +30); do
        rm "$file"
        ((deleted++))
done

echo "Compressed Files : $compressed"
echo "Deleted Files : $deleted"

```

### Task 2: Server Backup Script

```bash
#!/bin/bash

SOURCE=$1
DESTI=$2

if [ -z "$SOURCE" ] || [ -z "$DESTI" ]; then
        echo "Usage $0 <source_dir> <destination_dir>"
        exit 1
fi

if [ ! -d "$SOURCE" ]; then
        echo "$SOURCE directory doesn't exist"
        exit 1
fi

mkdir -p "$2"
echo "Backup Directory created $2"

timestamp=$(date +%Y-%m-%d)
archive="$DESTI/backup-$timestamp.tar.gz"

tar -cvzf "$archive" -C "$SOURCE" .
if [ -f "$archive" ]; then
        size=$(du -h "$archive" | cut -f1)
        echo "Backup created: $archive"
        echo "Size : $size"
else
        echo "Backup not created"
        exit 1
fi

find "$DESTI" -name "backup-*.tar.gz" -mtime +14 -delete

```

### Task 3: Crontab

health_check,.sh
```bash
#!/bin/bash

echo "===== HEALTH CHECK REPORT ====="
echo "Time: $(date)"
echo ""

# CPU Load
echo "---- CPU Load ----"
uptime
echo ""

# Memory Usage
echo "---- Memory Usage ----"
free -h
echo ""

# Disk Usage
echo "---- Disk Usage ----"
df -h
echo ""

# Top 5 processes (CPU)
echo "---- Top 5 CPU Processes ----"
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head -6
echo ""

echo "===== END OF REPORT ====="

```

0 2 * * * ./log_rotate.sh /var/log/nginx/ - ( Runs everyday at 2 AM )


0 3 * * 0 ./backup.sh /home/ec2-user/day_18 /home/ec2-user/backup_folder - ( Runs every sunday at 3 AM )


*/5 * * * * /home/ec2-user/day-19/health_check.sh >> /home/ec2-user/day-19/report.log 2>&1 - ( Runs every 5 mins ) 

### Task 4: Combine — Scheduled Maintenance Script

```bash
#!/bin/bash

LOG_FILE="/var/log/maintenance.log"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') - $1" >> "$LOG_FILE"
}

log "Maintenance started"

./log_rotate.sh /var/log/nginx/ >> "$LOG_FILE" 2>&1
./backup.sh /home/ec2-user/day_18 /home/ec2-user/backup_folder >> "$LOG_FILE" 2>&1

log "Maintenance completed"

```

