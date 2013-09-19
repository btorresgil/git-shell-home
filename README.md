Private Git Server
==================

## Introduction ##

This repository represents a home directory for a git user
which is used to store git repositories for a private git
server. Typically users would supply their ssh public key
to the server administrator to get access. The scripts in
this repository make it easy to create new repositories on
the server and setup new users by storing their SSH keys.

## Commands ##

These commands are available to an admin who SSH's into the
server with the `git` username:

- help:  show help text
- addkey:  add a public SSH key for a user, allowing them access to all repositories
- create:  create a new repository (specify the name as an argument of the command)
- list:  show all existing git repositories

## Installation ##

These steps set up a  private git server on Ubuntu in the /home/git directory.
You can change the /home/git directory to your prefered directory to store git
repositories.

#### Step 1:  Install git ####

    sudo apt-get install git

#### Step 2:  Create a `git` user and group on the server ####

    sudo adduser --no-create-home --shell /usr/bin/git-shell --disabled-password --home /home/git git

#### Step 3:  Clone this repo to the home directory

    sudo git clone https://github.com/dralth/git-shell-home /home/git

#### Step 4:  Set the first admin's public key ####

  If the admin is your user on the same server:

    sudo cp ~/.ssh/id_rsa.pub /home/git/.ssh/authorized_keys

  For other public keys:

    sudo sh -c 'echo "YOUR_SSH_KEY" > /home/git/.ssh/authorized_keys'

#### Step 5:  Set the permissions on the home directory ####

    sudo chown -R git:git /home/git

## More information ##

[Generating SSH keys] (https://help.github.com/articles/generating-ssh-keys)
[SSH key access with disabled password auth] (http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/)
