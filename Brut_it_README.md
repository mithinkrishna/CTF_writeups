1) Nmap revealed:
   PORT   STATE SERVICE VERSION
   22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
   80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
   MAC Address: 0A:FF:DC:C2:46:6F (Unknown)
   Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

2) Performed a Gobuster scan and found a hidden dir :
     1)/admin                (Status: 301)
     2)index.html            (Status: 200)

3) Using curl to retrieve the contents of /admin, it revealed the username as admin.

4) Used Hydra to brute-force the password. Password:xavier

5) Logged in to the /admin page and got the flag and private RSA key.

6) Used ssh2john and cracked the passphrase. Passphrase: rockinroll

7) SSHed in as user john with the passphrase and retrieved the flag located in info.txt.

8) Tried to escalate privileges to root user and found that this user has been given sudo (root privilege)
   for the cat.
    User john may run the following commands on bruteit:
    (root) NOPASSWD: /bin/cat

9) Used sudo cat /etc/shadows and found the root password in sha512crypt.

10) Retrieved the password in text using John. Password: football

11) Found the flag in root.txt.
