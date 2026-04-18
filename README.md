# Gitlab-homelab-project
Documentation of GitLab Installation and set up in a docker container. 

My reason for installing Gitlab is to learn how to write yaml, infrastructure as code, and utilize Gitlab runners for automation. It will be the source of truth for my homelab containing all the compose files for my containers. From there I can write a compose on my personal device, push it to Gitlab, pull it down on the server and run it. Because of Git, I can look at and keep a log of changes through previous commits. 

## Step 1: preparing volumes
- On my server I set up three files to attach to the Gitlab container, config, logs, and data.

## Step 2: Preparing Docker
- I ran into some issues making sure I could use docker compose on my server, and that it was the right version. I had to remove and download docker again to make sure I had the right version of docker compose.

## Step 3: Writing the Yaml
- I am still learning how to write yaml files, so I had some help from AI preparing the yaml. 

