# Description: Disctionary Attacks

### Note
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

### TODO
* None
