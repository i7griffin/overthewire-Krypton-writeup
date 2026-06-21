In this level the user is not given the execution and reading permission.
so the user is expected to create a temp directory and produce a link to the orriginal directory with the files to execute them 

Create a symbolic link to a directory:
bashln -s /path/to/original/directory /path/to/link/name
Example:
bashln -s /home/user/Documents /home/user/Desktop/DocLink
This creates a shortcut link called DocLink on the Desktop that points to the Documents folder.
Check if a link exists:
bashls -la /home/user/Desktop/DocLink
If it's a symlink, you'll see an arrow: DocLink -> /home/user/Documents
Remove a directory link:
bashrm /path/to/link/name
(Use rm, not rmdir — rmdir tries to delete the original directory)
Create a hard link (not recommended for directories):
bashln /path/to/original/directory /path/to/link/name
Note: Hard links to directories usually don't work on most systems unless you're root.
View all links in a directory:
bashls -la /path/to/directory
Symlinks show as: name -> /target/path


then execute the file to encrypt the meesage and then compared encrypted and decrypted message to find to total shift 
