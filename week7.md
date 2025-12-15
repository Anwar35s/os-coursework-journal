# 🔐 Week 7 – File Permissions, Ownership & Shell Scripting

## 📌 Overview

In Week 7, we explored Linux file permission systems and learned how to manage user access to files and directories through permission changes and ownership adjustments. We also used shell scripts to automate these tasks.

---

## 🧾 Step 1: Viewing File Permissions with `ls -l`

We used the `ls -l` command to list files with their permissions. This shows the file type, read/write/execute permissions for user, group, and others.

```bash
ls -l
📷 Screenshot:

🔧 Step 2: Changing Permissions Using chmod
We changed the permissions of a file using chmod. For example, giving execute permission to the user:

bash
Copy code
chmod u+x script.sh
We also tried numeric (octal) mode:

bash
Copy code
chmod 755 script.sh
📷 Screenshot:

👤 Step 3: Changing File Ownership with chown and chgrp
We learned how to change the ownership of files using chown and group ownership using chgrp.

bash
Copy code
sudo chown student:student example.txt
sudo chgrp users example.txt
📷 Screenshot:

⚙️ Step 4: Automating Permissions with Shell Script
We created a shell script that:

Creates a file

Changes permissions to 644

Changes ownership

Displays the final permission details

📜 file-permissions.sh
bash
Copy code
#!/bin/bash
echo "Creating file..."
touch example.txt

echo "Setting permissions to 644..."
chmod 644 example.txt

echo "Changing ownership to current user..."
sudo chown $USER:$USER example.txt

echo "Final file info:"
ls -l example.txt
📷 Screenshot:

🚀 Step 5: Making the Script Executable
To run the script, we made it executable using chmod +x:

bash
Copy code
chmod +x file-permissions.sh
./file-permissions.sh
📷 Screenshot:

📁 Step 6: Observing umask Defaults
We explored how the default permissions are set using umask.

bash
Copy code
umask
touch newfile.txt
ls -l newfile.txt
We observed that the default umask value (e.g., 0022) subtracts from the default 666 or 777 permissions.
