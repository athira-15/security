# Description: RouterHunterBR

### Introduction
* RouterHunterBR is a tool used to find vulnerable routers on a network. 
* It helps to identify vulnerabilities such as DNSChanger. DNSChanger vulnerability allows an attacker to change the 
  DNS server of the router to direct all the traffic to desired websites with malicious purposes.  
* RouterHunterBR is an automated security tool that finds vulnerabilities and performs tests on routers and vulnerable 
  devices on the Internet. It was designed to run over Internet looking for defined ips tracks or random in order to 
  automatically exploit the vulnerability DNSChanger on home routers.
* This script explores four vulnerabilities in routers, namely :
    - [Shuttle Tech ADSL Modem-Router 915 WM / Unauthenticated Remote DNS Change Exploit](https://www.exploit-db.com/exploits/35995)
    - [D-Link DSL-2740R/Unauthenticated Remote DNS Change Exploit](http://www.exploit-db.com/exploits/35917/)
    - [LG DVR LE6016D/Unauthenticated users/passwords disclosure exploit]( http://www.exploit-db.com/exploits/36014/)
    - [D-Link DSL-2640B Unauthenticated Remote DNS Change Exploitx](https://fortiguard.com/encyclopedia/ips/47763)

### Dependencies 
* RouterHunterBR.php script has the following dependencies:
```
sudo apt-get install curl libcurl3 libcurl3-dev php5 php5-cli php5-curl</i>
```

### Argument list
| Argument              | Meaning                                                       |
|-----------------------|---------------------------------------------------------------|
| --range               | Will set IP range that will be scanned. ex: 201.12.60.0-255   |
| --dns1 /dns2          | To specify DNS addresses                                      |
| --output              | To save output from standard output to a file                 |
| --threads 10          | Set threads numbers                                           |
| --rand                | Randomizing ips routers                                       |
| --limit-ip 10         | Define limit random ip                                        |
| --file                | Input a file containing a list of ip addresses to scan        |

### Usage Examples
```
# Simple search
php RouterHunterBR.php --range '177.100.255.1-20' --dns1  8.8.8.8 --dns2 8.8.4.4 --output result.txt

# Set IPS random
php RouterHunterBR.php --rand --limit-ip 200 --dns1  8.8.8.8 --dns2 8.8.4.4 --output result.txt

# Set source file
php RouterHunterBR.php --file ips.txt --dns1  8.8.8.8 --dns2 8.8.4.4 --output result.txt

# Set proxy
php RouterHunterBR.php --range '177.100.255.1-20' --dns1  8.8.8.8 --dns2 8.8.4.4 --output result.txt --proxy 'localhost:8118

# where proxy formats are as follows
--proxy 'localhost:8118'
--proxy 'socks5://googleinurl@localhost:9050'
--proxy 'http://admin:12334@172.16.0.90:8080'
```

