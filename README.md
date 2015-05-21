# Introduction

SSH keys are a way to identify trusted computers, without involving passwords. The steps below will walk you through generating an SSH key and using it to authenticate.


# How To

## Step 1: Check for SSH keys
```
# Lists the files in your .ssh directory, if they exist
$ ls -al ~/.ssh
```

> If you receive an error that the `~/.ssh` doesn't exist, everything is fine! We'll create it in Step 2.


## Step 2: Generate a new SSH key

Run in your terminal
```
# Creates a new ssh key, using the provided email as a label
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
and follow the instructions.

> Your ssh key should be unique. It's like a digital passport. This means that you should't create a new ssh key every time but use the same one all the time. For this reason you can keep the default `id_rsa` filename.


## Step 3: Add your key to the ssh-agent

Run in your terminal
```
# start the ssh-agent in the background
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
```

## Step 4: Use your SSH key
Run in your terminal
```
pbcopy ~/.ssh/id_rsa.pub
# Copies the contents of the id_rsa.pub file to your clipboard
```

### Use in GitHub
1. Login into your account
2. Click to `settings`
3. Click `SSH keys` and later `Add SSH Key`
  - In the Title field, add a descriptive label for the new key.
  - Paste your key into the "Key" field
4. Click Add key
5. Confirm the action by entering your GitHub password
6. Test the connection running in your terminal `ssh -T git@github.com`
