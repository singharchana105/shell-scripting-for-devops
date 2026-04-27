# Why shell-scripting-for-devops?

. Automates server setups(e.g - install packages, configure services)

# Basic Shell Script Structure
```
#!/bin/bash

echo "Hello, Devops!"

```

# 1. Install Packages
```
#!/bin/bash
sudo apt update && sudo apt install -y nginx

```

# 2. Monitor Disk Usages
```
#!/bin/bash

df -h > disk_usage_report.txt

purpose: server disk space usages to file for review later

```

# 3. Backup files
```
#!/bin/bash

tar -czf backup_$(date +%F).tar.gz/path/to/directory

Purpose: Compresses a directory into a .tar.gz backup file with the current date.

```
# 4. Jenkins Job Trigger
```
#!/bin/bash

curl -X POST http://jenkins.local/job/your-job-name/build \

--user your-user:your-api-token

Purpose: Triggers a Jenkins CI job remotely using a POST request and authentication.

```

# 5. Docker Container Health Check
```
#!/bin/bash

if docker ps | grep -q my_container; then

echo "Container is running"

else

echo "Container is down"

fi

Purpose: Checks if a specific Docker container (my_container) is running.

```
# 6. System Health Check

```
#!/bin/bash

echo "CPU Load:"; uptime

echo -e "\nMemory Usage:"; free -m

echo -e "\nDisk Usage:"; df -h

echo -e "\nTop 5 Memory Consuming Processes:"; ps aux --sort=-%mem | head -n 6

Purpose: Shows system metrics like CPU load, memory, disk, and top memory-consuming processes.

```

# 7. Service Restart on Failure

#!/bin/bash

SERVICE="nginx"

if! systemctl is-active --quiet $SERVICE; then 

echo "$SERVICE is down. Restarting..." 

      systemctl start $SERVICE 
else

echo "$SERVICE is running"

fi

Purpose: Checks if nginx service is down and restarts it automatically.

```

# 8. Log Rotation Script

#!/bin/bash

LOG_DIR="/var/log/myapp"

ARCHIVE_DIR="/var/log/myapp/archive"

mkdir -p $ARCHIVE_DIR

find $LOG_DIR/*.log -mtime +7-exec mv {} $ARCHIVE_DIR \;

gzip $ARCHIVE_DIR/*.log

Purpose: Moves logs older than 7 days to an archive and compresses them.

















