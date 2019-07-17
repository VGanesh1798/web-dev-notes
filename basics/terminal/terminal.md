# Basic Terminal Commands
These commands are for bash in particular since it's probably the best shell out there other than maybe zsh. With these commands you'll pretty much be set to start developing.

## Keyboard Shortcuts
`^C` - Cancel a command

`^D` - Close shell

`^L` - Clear screen

`^U` - Clear line 

## Navigation and Listing
```
pwd         # Print working directory
cd FOLDER   # Change directory to FOLDER
cd ..       # Move up one directory
cd -        # Change to last working directory
cd          # Change to user's home directory

ls          # List files
ls -a       # List all files
ls -l       # List files in a formatted list
```

## CRUD
```
mkdir FOLDER             # Creates FOLDER
touch FILE               # Creates FILE

cat FILE                 # Output FILE
less FILE                # Read FILE in less
head FILE                # Print first ten lines of FILE
tail FILE                # Print last ten lines of FILE

vim FILE                 # Open FILE in Vim
nano FILE                # Open FILE in Nano
cat > FILE               # Write inputs into FILE until cancelled
cat >> FILE              # Append inputs into FILE until cancelled
cp PATH/FILE PATH/FILE   # Copy FILE from one PATH to another
mv PATH/FILE PATH/FILE   # Can move or rename FILE

rm FILE                  # Deletes FILE, which can be an empty folder
rm -r FOLDER             # Recursive delete; deletes FOLDER and all contents
rm -rf FOLDER            # Forcefully delete FOLDER and all contents
```

## Other Tools
```
whoami          # Output your current user
clear           # Clears screen
yes TEXT        # Spams TEXT until cancelled; without an argument, spams 'y'

man COMMAND     # Manual page for COMMAND
which COMMAND   # Outputs where COMMAND is defined

ping URL        # Ping URL until cancelled
wget FILE       # Download FILE from a URL
curl URL        # Output contents of URL
```