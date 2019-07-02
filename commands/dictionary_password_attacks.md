# Description : Dictionary Password Attack

### Introduction
* A password is defined as a word or a random set of letters used as a secret to protect an account from unauthorised 
  access.
* A dictionary password attack is a way to test the possibility of security breach of a password-protected machine or a 
  server. 
* It tries to defeat an authentication mechanism by systematically entering each word in a dictionary to guess a 
  password.
* There are two ways to perform password dictionary attack, namely Online and Offline.
    - Online password dictionary attack: It can be performed when the target machine is online. A pentester uses the 
      same interface as a regular user to try to gain access to accounts. A curated list of possible passwords is 
      required to conduct this attack.
    - Offline password dictionary attack: In order to perform an offline dictionary attack, a pentester tries to 
      establish access into password storage file (such as: etc/shadow file of linux) from a target system. This 
      approach is adopted in the following scenarios
        - when the pentester has local access to target file or system.
        - when there is no limit in the number of failed attempts that can be made.
        - when the pentester has a bunch of tools available to automate the attack.
        - when the pentester has a combination of previously acquired password lists, directories etc.

### Tools
* hydra
* patator
* sqldict

### Hydra
* Hydra (also known as 'thc-hydra') is an online password attack tool. It brute forces various combinations on live 
services like ftp, telnet, ssh, http, smb etc.
* Syntax
```
hydra [[[-l LOGIN|-L FILE] [-p PASS|-P FILE]] | [-C FILE]] [-e nsr] [-o FILE] [-t TASKS] [-M FILE [-T TASKS]] [-w TIME] [-W TIME] [-f] [-s PORT] [-x MIN:MAX:CHARSET] [-c TIME] [-ISOuvVd46] [service://server[:PORT][/OPT]]
```
* Options

| Option   |   Meaning |
|-----------|-------------|
| -l LOGIN or -L FILE   |   login with random LOGIN name or load several logins from a FILE |
| -p PASS or -P FILE    |   try password PASS, or load several passwords from FILE          |
| -C FILE               |   use a FILE with a list of colon separated "login:pass" format   |
| -e nsr                |   try "n" null password, "s" login as pass and/or "r" reversed login |
| -o FILE               |   write found login/password pairs to FILE |
| -t TASKS              |   run TASKS number of connects in parallel per target (default: 16)   |
| -T TASKS              |   run TASKS connects in parallel overall (for -M, default:64) |
| -M FILE               |   list of servers to attack, one entry per line, ':' to specify port  |
| -w / -W TIME          |   wait time for a response (32) / between connects per thread |
| -f / -F               |   exit when a login/pass pair is found (-M: -f:per host, -F:global)   |
| -s PORT               |   if the service is on different default port, mention it |
| -x MIN:MAX:CHARSET    |   password bruteforce generation
| -c TIME               |   wait time per login attempt over all threads |
| -ISOuvVd46            |   -I:Ignore an existing restore file, -S:perform an SSL connect, -O:use old SSLv2 and SSLv3, -u:loop around users, <br> -v/-V/-d:verbose mode/show login+pass for each attempt/debug mode |
| -service              |   the service to test |
| -server               |   the target: DNS, IP address |
| -OPT                  |   some service modules support additional input |

* Usage
```
# TODO
hydra -l root -P password_worst_password_list_2018.txt mysql://192.168.190.154

# TODO
hydra -L userlist.txt -p one_random_password imap://192.168.0.1/PLAIN

# TODO
hydra -l admin -p password ftp://[192.168.0.0/24]/

# TODO
hydra -L logins.txt -P password.txt -M targets.txt ssh
```

### Patator
* Patator is an another useful tool that allows to brute force multiple types of logins and even ZIP passwords.
* Available modules are:

| Module            |   Meaning                                                     |
|-------------------|---------------------------------------------------------------|
| ftp_login         | Brute-force FTP                                               |
| ssh_login         | Brute-force SSH                                               |
| telnet_login      | Brute-force Telnet                                            |
| smtp_login        | Brute-force SMTP                                              |
| smtp_vrfy         | Enumerate valid users using SMTP VRFY                         |
| smtp_rcpt         | Enumerate valid users using SMTP RCPT TO                      |
| finger_lookup     | Enumerate valid users using Finger                            |
| http_fuzz         | Brute-force HTTP                                              |
| ajp_fuzz          | Brute-force AJP                                               |
| pop_login         | Brute-force POP3                                              |
| pop_passd         | Brute-force poppassd (http://netwinsite.com/poppassd/)        |
| imap_login        | Brute-force IMAP4                                             |
| ldap_login        | Brute-force LDAP                                              |
| smb_login         | Brute-force SMB                                               |
| smb_lookupsid     | Brute-force SMB SID-lookup                                    |
| rlogin_login      | Brute-force rlogin                                            |
| vmauthd_login     | Brute-force VMware Authentication Daemon                      |
| mssql_login       | Brute-force MSSQL                                             |
| oracle_login      | Brute-force Oracle                                            |
| mysql_login       | Brute-force MySQL                                             |
| mysql_query       | Brute-force MySQL queries                                     |
| rdp_login         | Brute-force RDP (NLA)                                         |
| pgsql_login       | Brute-force PostgreSQL                                        |
| vnc_login         | Brute-force VNC                                               |
| dns_forward       | Forward DNS lookup                                            |
| dns_reverse       | Reverse DNS lookup                                            |
| snmp_login        | Brute-force SNMP v1/2/3                                       |
| ike_enum          | Enumerate IKE transforms                                      |
| unzip_pass        | Brute-force the password of encrypted ZIP files               |
| keystore_pass     | Brute-force the password of Java keystore files               |
| sqlcipher_pass    | Brute-force the password of SQLCipher-encrypted databases     |
| umbraco_crack     | Crack Umbraco HMAC-SHA1 password hashes                       |
| tcp_fuzz          | Fuzz TCP services                                             |
| dummy_test        | Testing module                                                |

* Syntax
* patator -h
* patator <module_name> --help

####Module Options
Module name  | Option:Meaning |
|------------|------------------------|
|ftp_login   |host:target host, port:target port[21], user:usernames to test, password:passwords to test, tls:use TLS[0 or 1], timeout:seconds to wait for a response[10], persistent:use persistent connections[1 or 0] <br> -x arg:actions and conditions  |
|ssh_login   |host:target host, port:target port[22], user:usernames to test, password:passwords to test, auth_type:type of password authentication to use [password or keyboard-interactive or auto], keyfile:file with RSA, DSA or ECDSA private key to test, <br> persistent:use persistent connections[1 or 0], x arg:actions or conditions |
|mysql_login |host:target host, port:target port[3306], user:usernames to test, password:passwords to test, timeout:seconds to wait for a response[10], -x arg:actions and conditions | 
|smtp_login  |persistent:use persistent connections[1 or 0], timeout:seconds to wait for a response[10], host:target host, port:target port[25], ssl:use SSL[0 or 1], helo:helo or ehlo command to send after connect[skip], starttls:send STARTTLS[0 or 1], user:usernames to test, password:passwords to test |

 <i>Note : All modules have its own customised options list, which can be viewed by using: 
 <b>patator <module_name> --help</b></i>
 
####Usage Examples
* ftp_login host=10.0.0.1 user=FILE0 password=FILE1 0=logins.txt 1=passwords.txt -x ignore:mesg='Login incorrect.' -x ignore,reset,retry:code=500

* ssh_login host=10.0.0.1 user=root password=FILE0 0=passwords.txt -x ignore:mesg='Authentication failed.'

* mysql_login host=10.0.0.1 user=FILE0 password=FILE1 0=logins.txt 1=passwords.txt -x ignore:fgrep='Access denied for user.'

* smtp_login host=10.0.0.1 user=f.xxx@yyy.com password=FIE0 0=passwords.txt [helo='hi'] -x ignore:fgrep='Authentication failed.' -x ignore,reset,retry:code=421
