---
publish: true
title: How to backup N8N selfhosted Docker
created: 2025-08-19
modified: 2025-08-19
tags:
  - recipes
  - n8n
  - backup
cssclasses: ""
---

## Setting up the backup environment
### Setting up a encryption key
- Find the encryption key. It is inside the file `~/.n8n/config` inside the n8n Docker container
- Set the environment variable `N8N_ENCRYPTION_KEY` to the encryption key under the `environment` section in the Docker compose file.


### Setting up Git and Github 
- Create a git repository in folder `~/backup/n8n_backup`
- Create a new repository on Github : `n8n_backup`
``` bash
# Push an existing repository from the command line
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:craftsmandigital/n8n_backup.git
git push -u origin main
```
## Steps in the backup process
- Copy compose.yaml and .env to back it up
- Export n8n workflows to a folder inside container
- Same as above with the credentials
- Copy workflows/credentials to the host machine on a git maintained folder
- Push the backup to GitHub

```bash
# Copy compose.yaml to back it up
cp /opt/stacks/n8n/compose.yaml ~/backup/n8n_backup/
# Remember to delete encryption key inside .env
cp /opt/stacks/n8n/.env ~/backup/n8n_backup/

#copy all workflows to a folder inside container
docker exec -u node -it n8n-n8n-1 n8n export:workflow --backup --output=/tmp/backup/workflows

#copy credentials to a folder inside container
docker exec -u node -it n8n-n8n-1 n8n export:credentials --backup --output=/tmp/backup/credentials
# copy credentials in plain text without encryption omiting "--decrypted" flag
#docker exec -u node -it n8n-n8n-1 n8n export:credentials --#backup --decrypted --output=/tmp/backup/credentials

#copy the credentials and workflows from the docker container to a folder maintainded by git on the server outside the container
docker cp n8n-n8n-1:/tmp/backup/. ~/backup/n8n_backup

# Go to backupfolder for pushing to github
cd ~/backup/n8n_backup
git add .
git commit -m "N8N Backup $(date +%Y-%m-%d_%H:%M:%S)"
git push
```

## Steps to restore backup to n8n
- Clone backup from GitHub
- Copy content of the backup from host machine, into the Docker container
- Import the credentials inside Docker container, into n8n
- Import the workflows inside Docker container, into n8n


``` bash
# Go to backup folder
cd ~/backup

# clone resent backup from gitt 
git clone git@github.com:craftsmandigital/n8n_backup.git

# copy the backup inside the n8n container
docker cp ~/backup/n8n_backup/. n8n-n8n-1:/tmp/restore 

# Import credentials
docker exec -u node -it n8n-n8n-1 n8n import:credentials --separate --input=/tmp/restore/credentials

# Import workflows
docker exec -u node -it n8n-n8n-1 n8n import:workflow --separate --input=/tmp/restore/workflows
```