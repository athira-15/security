# Description: Patator


* Patator is an another useful tool that allows to brute force multiple types of logins and even ZIP passwords.
* Available modules are 

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
 -----------------------------------------------------------------------------------
* The general syntax
````
> patator -h
> patator <module_name> --help
````
* Available module options are

 |Module name  | Option:Meaning                                                                                                                                                                                                                                                                                                                     |
 |-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
 | ftp_login   | host:target host, port:target port[21], user:usernames to test, password:passwords to test, tls:use TLS[0 or 1], timeout:seconds to wait for a response[10], persistent:use persistent connections[1 or 0] <br> -x arg:actions and conditions                                                                                      |
 | ssh_login   | host:target host, port:target port[22], user:usernames to test, password:passwords to test, auth_type:type of password authentication to use [password or keyboard-interactive or auto], keyfile:file with RSA, DSA or ECDSA private key to test, <br> persistent:use persistent connections[1 or 0], x arg:actions or conditions  |
 | mysql_login | host:target host, port:target port[3306], user:usernames to test, password:passwords to test, timeout:seconds to wait for a response[10], -x arg:actions and conditions                                                                                                                                                            | 
 | smtp_login  | persistent:use persistent connections[1 or 0], timeout:seconds to wait for a response[10], host:target host, port:target port[25], ssl:use SSL[0 or 1], helo:helo or ehlo command to send after connect[skip], starttls:send STARTTLS[0 or 1], user:usernames to test, password:passwords to test                                  |
 ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
 * All modules have its own customised options list, which can be viewed by using 
 ````
  patator <module_name> --help
 ````
 * Usage 
 ````
 # Given a target IP, username list, password list,  bruteforce login attempt into ftp service 
   ftp_login host=10.0.0.1 user=FILE0 password=FILE1 0=logins.txt 1=passwords.txt -x ignore:mesg='Login incorrect.' -x ignore,reset,retry:code=500

# Given a target IP, username, password list, bruteforce login attempt into ssh service
   ssh_login host=10.0.0.1 user=root password=FILE0 0=passwords.txt -x ignore:mesg='Authentication failed.'

# Given a terget IP, username list, password list, bruteforce login attempt into MySQL service
   mysql_login host=10.0.0.1 user=FILE0 password=FILE1 0=logins.txt 1=passwords.txt -x ignore:fgrep='Access denied for user.'

# Given a target IP, username and a password list, bruteforce login attempt into smtp service
   smtp_login host=10.0.0.1 user=FILE0@yyy.com 0=logins.txt password=FILE0 0=passwords.txt [helo='hi'] -x ignore:fgrep='Authentication failed.' -x ignore,reset,retry:code=421
````