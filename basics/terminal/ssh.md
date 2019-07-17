# SSH Commands
SSH stands for **S**ecure **Sh**ell and is a protocol to login to remote systems securely, as the name suggests. SSH can be used for remote Git authentication as well.

## SSH Basics
To connect to a remote server (that you hopefully have access to), use `ssh USER@SERVER` and login using your password. That's it.

The first time you connect to a remote server, you will get a warning that the authenticity of the host cannot be established, followed by the RSA key fingerprint. If this fingerprint looks correct for the host, type `yes` to continue connecting and add the server to your list of known hosts.

## Adding SSH Key to GitHub
Make sure you don't already have a GitHub SSH key by running `ls -al ~/.ssh`. If the .ssh folder doesn't exist, it will after you either create a new key or connect to a remote server. If you already have keys and want to use a pair for GitHub, you can do so.

If you instead want to create a new SSH key for GitHub, run `ssh-keygen -t rsa -b 4096 -C EMAIL`. This will create a private/public key pair, which you can rename from the default which is id_rsa. Type in a secure passphrase for the key.

To add this new key to the ssh-agent, run `eval $(ssh-agent -s)` or add a special script to your .bashrc file to automatically start the ssh-agent whenever bash is loaded. Now, add your private key to the agent with `ssh-add ~/.ssh/PRIVATE_KEY`.

Add the public key's contents to your clipboard and paste it into the new SSH key on GitHub.

To test the connection, run `ssh -T git@github.com` and type `yes` to continue past the authentication warning after confirming the RSA key fingerprint. Your GitHub username should appear in a message following this.

To change a passphrase, run `ssh-keygen -p` and type the private key whose passphrase you want to change. Change it this way.

If you add the script to .bashrc, you won't have to enter your passphrase everytime you use your SSH key, just the one time you login to a new bash shell.

## Cloning Repo via SSH

After adding an SSH key to GitHub, you have the ability to clone a repo over SSH instead of HTTPS. Doing so will take advantage of your new key and require you to use your passphrase (unless you choose otherwise) whenever you communicate with GitHub, like when cloning pushing, pulling, etc.