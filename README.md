1) Nmap scan revealed:
    PORT     STATE SERVICE    VERSION
    22/tcp   open  ssh        OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
    53/tcp   open  tcpwrapped
    8009/tcp open  ajp13      Apache Jserv (Protocol v1.3)
    8080/tcp open  http       Apache Tomcat 9.0.30
    MAC Address: 0A:FF:C9:30:C7:19 (Unknown)
    Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

  2) Found Apache Tomcat is vulnerable to CVE-2020-1938.

  3) Used Metasploit
     auxiliary/admin/http/tomcat_ghostcat  2020-02-20       normal  Yes    Apache Tomcat AJP File Read

     Retrieved the username and password. skyfuck:8730281lkjlkjdqlksalks

  5) SSHed to the target machine and found the flag in user.txt.
     
  6) Found credential.pgp and tryhackme.asc in the home directory of the user.

  7) Converted the PGP to base64, transferred it to my attack machine, and decrypted it back to PGP.
     Converted the PGP private key to a PGP hash, then decrypted the PGP hash using John.
     Passphrase obtained from tryhackme.asc: Alexandru
     
  8) This passphrase was later used to decrypt the credential.pgp
     credentials.pgp was for a user merlin:asuyusdoiuqoilkda312j31k2j123j1g23g12k3g12kj3gk12jg3k12j3kj123j.

  9) SSHed in as user merlin and found it had root privilege for /usr/bin/zip.

  10) Privileges were escalated using this to root, and the flag was obtained in root.txt.
