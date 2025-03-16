### Add GitHub SSH Key to Server for Access

This playbook takes your github.pub key and adds them to the target server to allow for ssh.
This can be used to create a ssh key for login from a machine or for ansible (Two seperate keys are recommended)

### Steps to setup SSH key Github
1. Generate a new SSH key using: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=windows
2. Go to https://github.com/settings/keys and enter the public key there.
3. (For machine login to prevent passphrase prompt) Run ssh-add ~/.ssh/{SSH_PRIV_KEY} to add the key to yout store

### Note
In order to use this playbook you will need to log into the server with user and pass. After that you can use the ssh key. 

### TODO 
- Turn github url into variable