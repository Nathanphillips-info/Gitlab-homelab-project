# GitLab Homelab Project

## Overview
This project documents the deployment of GitLab in a Docker environment as part of my homelab.

The goal is to:
- Learn infrastructure as code and YAML configuration
- Manage services using Docker Compose
- Use GitLab as a central source of truth for homelab configurations
- Explore CI/CD and automation with GitLab Runners

This setup allows me to write configurations locally, push them to GitLab, and deploy them on my server.

---

## Technologies Used
- Docker / Docker Compose
- GitLab CE
- (In progress) Traefik for reverse proxy

---

## Step 1: Preparing Volumes
Created persistent directories on the host system to store GitLab data:

- config → `/etc/gitlab`
- logs → `/var/log/gitlab`
- data → `/var/opt/gitlab`

These volumes ensure data persists across container restarts.

---

## Step 2: Preparing Docker
Verified Docker and Docker Compose were properly installed.

- Encountered version issues with Docker Compose
- Reinstalled Docker to ensure compatibility with Compose

---

## Step 3: Writing the Docker Compose File
Created a Docker Compose configuration to deploy GitLab.

- Defined volumes for storage
- Configured networking for container communication
- Set GitLab external URL

Deployed the container:

```bash
docker compose up -d
```

## Step 4: Initial Login

GitLab generates a temporary root password on first startup.

Username: root
Retrieve password:
docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password

This file is automatically deleted after 24 hours.
It is recommended to change the password immediately after first login.

## Step 5: Configure GitLab
Created user accounts
Adjusted settings as needed
Added SSH key for authentication

To add an SSH key:

Navigate to: User Settings / Preferences / Access / SSH Keys
Paste your public key
Step 6: Test Repository

Created a test repository to verify functionality.

Initialize repository:

git init

Add a file:

git add <file_name>

Commit changes:

git commit -m "initial commit"

Add remote origin:

git remote add origin <repository_url>

Push to GitLab:

git push origin main

---

### Notes
GitLab is resource-intensive and benefits from sufficient RAM and storage
Reverse proxy (Traefik) integration is planned for cleaner domain-based access
Future Improvements
Configure Traefik for HTTPS and domain routing
Integrate GitLab Runners for CI/CD pipelines
Expand automation using GitLab pipelines
