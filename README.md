# Gitlab-homelab-project
Documentation of GitLab Installation and set up in a docker container. 

My reason for installing Gitlab is to learn how to write yaml, infrastructure as code, and utilize Gitlab runners for automation. It will be the source of truth for my homelab containing all the compose files for my containers. From there I can write a compose on my personal device, push it to Gitlab, pull it down on the server and run it. Because of Git, I can look at and keep a log of changes through previous commits. 

## Step 1: preparing volumes
- On my server I set up three files to attach to the Gitlab container, config, logs, and data.

## Step 2: Preparing Docker
- I ran into some issues making sure I could use docker compose on my server, and that it was the right version. I had to remove and download docker again to make sure I had the right version of docker compose.

## Step 3: Writing the Yaml
- I am still learning how to write yaml files, so I had some help from AI preparing the yaml.
- Once it was prepared and the volumes and networking were correct, I ran docker compose up -d
- I am still getting Traefik set up so I have nice domain names for my self hosted services, so I connected through the socket.

## Step 4: Connecting to the web UI and setting up your account. 
- for intiial set up you will need to access the password for the web ui which is in the etc/gitlab files.
- the username is root
- To access the password you can run this command: docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
- This file is automatically deleted after 24 hours, so on first sign in, you should change the credentials.

## Step 5: Configure Gitlab
- Next you can add accounts for access, and change the settings how you would like.
- I would add a ssh key for pushing to gitlab. You can add the public key by clicking on your account/preferences/access/ssh_keys
- Then you can copy the public key.

## Step 6: Test project
- You can create a test project and try pushing some code or text to Gitlab to make sure it works.
- In root of the test project file you can run: git init, this will initialize the repo
- Then type some text or code in a file and run from the command line: git add <your_file_name>
- Next you can commit the change: git commit -m "explain the commit"
- Add a remote origin to the repo so it can connect to Gitlab, there are two ways to do this, but I usually make the repo in Gitlab, uncheck readme, and use the given url or ssh line under clone wiht http or ssh.
- In the command line run: git remote add origin <the_cloned_line>
- Finally push the changes and see if the code is in Gitlab: git push origin main, it will either be main or master depending on what the branch is called. 

