# Deploying an Apache Web Server on an Azure Linux VM

This note covers installing Apache on an Azure Linux VM, verifying that it is running, connecting to the VM over SSH from Mac and Windows (including the Windows private key permission fix), copying files to the VM with `scp`, and publishing a page through Apache.

---

## 1. Install and Start Apache (Bash Script)

Run these commands on the VM (or paste them as a startup script).

```bash
#!/bin/bash
sudo apt update -y
sudo apt install -y apache2
sudo systemctl start apache2
sudo systemctl enable apache2
echo "<html><h1>Welcome to Apache Web Server on Azure VM!</h1></html>" | sudo tee /var/www/html/index.html
```

### Line-by-line explanation

| Command | Purpose |
| --- | --- |
| `#!/bin/bash` | Shebang line. Tells the system to run the script with the Bash shell. |
| `sudo apt update -y` | Refreshes the package list. `-y` answers "yes" to prompts automatically. |
| `sudo apt install -y apache2` | Installs the Apache HTTP server package. |
| `sudo systemctl start apache2` | Starts the Apache service right now. |
| `sudo systemctl enable apache2` | Makes Apache start automatically every time the VM boots. |
| `echo "..." \| sudo tee /var/www/html/index.html` | Writes the HTML text into Apache's default web page. |

### Why `tee` is used

`/var/www/html` is owned by root. In `sudo echo "..." > file`, the `sudo` applies only to `echo`, while the `>` redirection is performed by your normal user, so it fails with "Permission denied". Piping into `sudo tee` makes the write itself run as root.

`/var/www/html/index.html` is the default page Apache serves from its document root.

---

## 2. Verify the Web Server

### 2.1 Check the service status

```bash
systemctl status apache2
```

Look for `active (running)` in the output. Press `q` to exit the status view.

### 2.2 Check that port 80 is listening

```bash
sudo ss -tulpn | grep :80
```

| Option | Meaning |
| --- | --- |
| `ss` | Displays socket (network connection) information. |
| `-t` | Show TCP sockets. |
| `-u` | Show UDP sockets. |
| `-l` | Show only listening sockets. |
| `-p` | Show the process that owns each socket. |
| `-n` | Show numeric ports instead of service names. |
| `grep :80` | Filters the output to lines containing port 80 (the default HTTP port). |

A line showing `apache2` listening on port 80 confirms the server is bound to the port.

### 2.3 Check that the server responds

```bash
curl http://localhost:80
```

`curl` sends an HTTP request to the VM itself. If Apache is working, the HTML from `index.html` is printed in the terminal.

---

## 3. Connect to the VM Using SSH

The VM is accessed with the private key (`.pem` file) that was downloaded when the VM was created. SSH refuses to use a private key that other users on the computer can read, so the key's permissions must be restricted first.

### 3.1 From a Mac (or Linux) terminal

1. In the Azure portal, open the VM and use the **Connect** option to get the ready-made SSH command.
2. Bypass the permission warning by restricting the key file:

```bash
chmod 400 <path of your pem file>
```

`chmod 400` gives the file owner read-only access and removes all access for the group and others.

3. Run the SSH command copied from the Azure portal.

### 3.2 From a Windows Command Prompt

#### Step 1: Fix the private key permissions (only if you get the error)

Running SSH with a key that is too open produces:

```text
WARNING: UNPROTECTED PRIVATE KEY FILE!
Permissions for 'myWebserver_key.pem' are too open.
This private key will be ignored.
Bad permissions. Try removing permissions for user: BUILTIN\Users
```

This happens because the `.pem` file is accessible by other Windows users or groups (for example the built-in `Users` group). Windows tools do not use `chmod`; the `icacls` command is used instead to view and modify file permissions.

Open **Command Prompt** (press `Windows + S`, search for Command Prompt, right-click, and choose **Run as administrator** if you get an "Access is denied" message), then run these commands one by one:

```cmd
icacls "<path of your pem file>" /inheritance:r
```

Removes the permissions the file inherits from its parent folder.

```cmd
icacls "<path of your pem file>" /remove "Users"
```

Removes the built-in `Users` group, which is the group named in the SSH error.

```cmd
icacls "<path of your pem file>" /grant:r "%USERNAME%:R"
```

Gives only your current Windows account read (`R`) permission. `%USERNAME%` is replaced automatically by the logged-in username (for example `HP`), and `/grant:r` replaces any existing explicit permission for that user.

Verify the result:

```cmd
icacls "<path of your pem file>"
```

Only your account should be listed, with `(R)`, similar to `HP:(R)`. The `Users` group must not appear.

| Option | Purpose |
| --- | --- |
| `icacls` | View and modify Windows file permissions. |
| `/inheritance:r` | Remove inherited permissions. |
| `/remove` | Remove a specific user's or group's permissions. |
| `/grant:r` | Grant a permission and replace existing explicit ones for that user. |
| `%USERNAME%` | The current Windows username. |
| `:R` | Read permission. |
| `/reset` | Reset the file's permissions to the inherited defaults. |

**If the commands above do not fix the error**, reset the permissions and apply them again:

```cmd
icacls "<path of your pem file>" /reset
icacls "<path of your pem file>" /inheritance:r
icacls "<path of your pem file>" /grant:r "%USERNAME%:R"
```

`/reset` clears complicated or incorrect existing permissions, and the next two commands lock the file down again.

#### Why SSH insists on this

A `.pem` file is a private key used to authenticate you to the VM. If other users on the same computer can read it, they could use it to log in to the VM as you. SSH therefore ignores any key that is not private to its owner.

#### Step 2: Connect

```cmd
ssh -i "<path of your ssh file>" azureuser@<ip of your virtual machine>
```

| Part | Meaning |
| --- | --- |
| `ssh` | Starts an SSH connection. |
| `-i` | Identity file: selects which private key to authenticate with. |
| `"<path of your ssh file>"` | Location of the private key (`.pem`) file. Quotes are needed if the path contains spaces. |
| `azureuser` | Username on the Azure Linux VM. |
| `<ip of your virtual machine>` | Public IP address of the VM, shown on the VM's overview page in the Azure portal. |

On success, a Linux shell prompt appears, similar to:

```text
azureuser@myWebserver:~$
```

---

## 4. Copy a File from the Local Machine to the Azure VM

Use `scp` (secure copy), which works over SSH and uses the same private key. Run it on your **local machine**, not inside the VM.

```bash
scp -i "<path of your ssh file>" "<path of file to be copied>" azureuser@<ip of your virtual machine>:<where to copy, e.g. /home/azureuser>
```

| Part | Meaning |
| --- | --- |
| `scp` | Secure copy over SSH. |
| `-i "<path of your ssh file>"` | Private key used for authentication. |
| `"<path of file to be copied>"` | Source: the file on your local machine. |
| `azureuser@<ip>:<destination>` | Target: the VM user, the VM IP, and the destination folder after the colon. |

The home folder `/home/azureuser` is used as the destination because `azureuser` can write there without `sudo`.

---

## 5. Run (Publish) Your File on the Web Server

After the file is on the VM, log in with SSH and copy it into Apache's document root:

```bash
sudo cp index.html /var/www/html
```

`sudo` is required because `/var/www/html` is owned by root. This replaces the default `index.html` with your own page, and Apache serves it immediately without a restart. Verify with:

```bash
curl http://localhost:80
```

---

## Quick Command Reference

| Task | Command |
| --- | --- |
| Install Apache | `sudo apt install -y apache2` |
| Start Apache | `sudo systemctl start apache2` |
| Start Apache on boot | `sudo systemctl enable apache2` |
| Check service status | `systemctl status apache2` |
| Check port 80 | `sudo ss -tulpn \| grep :80` |
| Test server locally | `curl http://localhost:80` |
| Restrict key (Mac/Linux) | `chmod 400 <path of your pem file>` |
| Restrict key (Windows) | `icacls "<path>" /inheritance:r`, `/remove "Users"`, `/grant:r "%USERNAME%:R"` |
| Connect (Windows) | `ssh -i "<path of your ssh file>" azureuser@<ip>` |
| Copy file to VM | `scp -i "<key>" "<local file>" azureuser@<ip>:/home/azureuser` |
| Publish file | `sudo cp index.html /var/www/html` |