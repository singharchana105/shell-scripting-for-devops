# Why shell-scripting-for-devops?

. Automates server setups (e.g - install packages, configure services)

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

```
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

```

#!/bin/bash

LOG_DIR="/var/log/myapp"

ARCHIVE_DIR="/var/log/myapp/archive"

mkdir -p $ARCHIVE_DIR

find $LOG_DIR/*.log -mtime +7-exec mv {} $ARCHIVE_DIR \;

gzip $ARCHIVE_DIR/*.log

Purpose: Moves logs older than 7 days to an archive and compresses them.

```

# 9. Git Auto Pull

```
#!/bin/bash

cd /home/ubuntu/my-repo

git pull origin main

Purpose: Automatically pulls the latest code from GitHub (useful with cron jobs).

```

# 10. Docker Cleanup Script

```

#!/bin/bash

docker container prune -f

docker image prune -f

docker volume prune -f

Purpose: Frees disk space by removing unused Docker containers, images, and volumes.

Note : prune this command is used for clean/remove/delete unused container,images,network.

```


# 11. PostgreSQL Database Backup

```

#!/bin/bash

BACKUP_DIR="/backups"

DB_NAME="mydb"

USER="postgres"

mkdir -p $BACKUP_DIR

pg_dump -U $USER $DB_NAME > $BACKUP_DIR/${DB_NAME}_$(date +%F).sql

Purpose: Creates a daily backup of a PostgreSQL database.

```


# 12. Kubernetes Pod Status Checker

```

#!/bin/bash

NAMESPACE="default"

kubectl get pods -n $NAMESPACE | grep -v Running

Purpose: Lists non-running pods in a Kubernetes namespace.

```

# 13 Jenkins Job Trigger with Token

```
#!/bin/bash

JENKINS_URL="http://jenkins.local"

JOB_NAME="my-job"

USER="your-user"

API_TOKEN="your-token"

curl -X POST "SJENKINS_URL/job/SJOB_NAME/build" --user $USER:SAPI_TOKEN

Purpose: Triggers a Jenkins job using username + token for security.

```

# 14. Check Port Availability

```

#!/bin/bash

PORT=8080

if Isof-i:SPORT > /dev/null; then

echo "Port SPORT is in use." else

fi

echo "Port SPORT is free."

Purpose: Checks if a specific port (like 8080) is being used by any process.

```

# 15. Kubernetes Rolling Restart

```

#!/bin/bash

DEPLOYMENT="myapp"

NAMESPACE="default"

kubectl rollout restart deployment $DEPLOYMENT -n $NAMESPACE

Purpose: Triggers a rolling restart of a Kubernetes deployment.

Use: Used to apply changes to a deployment (like new code) without downtime.

```

# 16. Pull Latest Docker Image and Restart Container

```
#!/bin/bash

IMAGE="myrepo/myapp:latest"

CONTAINER="myapp"

docker pull $IMAGE

docker stop $CONTAINER

docker rm SCONTAINER

docker run -d --name $CONTAINER -p 80:80 $IMAGE

Purpose: Pulls the latest Docker image, stops the existing container, removes it, and then restarts the container with the updated image.

Use: Ideal for CI/CD pipelines that require container updates.

```

# 17. Terraform Plan & Apply with Auto-Approval

```
#!/bin/bash

cd/path/to/terraform

terraform init

terraform plan -out=tfplan

terraform apply -auto-approve tfplan

Purpose: Automates the process of running terraform plan and applying the changes without manual approval.

Use: Useful for environments that require continuous infrastructure deployment.

```

# 18. Ansible Playbook Trigger

```

#!/bin/bash

ansible-playbook -i inventory.ini site.yml --limit web_servers

Purpose: Executes an Ansible playbook on a set of hosts defined by web_servers in the inventory file.

Use: Automates configuration management tasks like provisioning or deploying on specific servers.

```

# 19. Monitor CPU Usage and Send Alert

```

#!/bin/bash

THRESHOLD=80

CPU_LOAD=$(top-bn1 | grep "Cpu(s)" | awk '{print $2 + $4}')

if (($(echo "$CPU_LOAD > $THRESHOLD" | bc -l))); then

echo "High CPU Load: $CPU LOAD%" mail -s "Alert: CPU Load" admin@example.com

fi

Purpose: Monitors the CPU usage and sends an email alert if it exceeds the threshold (80% in this case).

Use: Ideal for alerting system administrators about high CPU usage.

```










