# Description : SSH Security Testing 

### References
* [About Nmap NSE](https://nmap.org/book/man-nse.html)
* [Nmap ssh2-enum-algos](https://nmap.org/nsedoc/scripts/ssh2-enum-algos.html)
* [Nmap ssh-brute](https://nmap.org/nsedoc/scripts/ssh-brute.html)
* [SSH-Audit : Installation And Usage Reference](https://github.com/arthepsy/ssh-audit) 
* [SSH-Audit : Introduction and Sample Usage](https://hackerific.net/2017/04/23/ssh-audit---a-tool-for-checking-ssh-server-security/)
* [SSH_Scan Installation and Usage Reference](https://github.com/mozilla/ssh_scan)
* [SSH_Scan : A Prototype SSH Configuration and Policy Scanner](https://www.2daygeek.com/ssh_scan-a-prototype-ssh-configuration-and-policy-scanner-for-linux/)

### Introduction
* SSH or Secure Socket Shell was developed by SSH Communications Security Ltd. 
* It's a network protocol that provides strong authentication and secure communications over insecure channels.
* It's a replacement for rlogin, rsh, rcp and rdist.
* Secure Socket Shell allows 
    - To securely log into another computer over a network.
    - To securely execute commands in a remote machine.
    - To securely move files from one machine to another.
* SSH refers both to the cryptographic network protocol and to the suite of utilities that implement this protocol. 
* SSH uses the client-server model, connecting a secure shell client application (the end at which the session is 
  displayed) with a SSH serverSSH (the end at which the session runs). It protects a network from attacks such as IP 
  spoofing, IP source routing, DNS spoofing etc.
* SSH Security Testing Methodologies
    - Nmap NSE Scripts
    - ssh_scan
    - ssh-audit
    
### Nmap NSE Scripts
* The Nmap Scripting Engine (NSE) is one of Nmap's most powerful and flexible features. 
* These scripts are written in Lua programming language. NSE scripts helps to automate a wide variety of networking 
  tasks. 
* NSE scripts available in Nmap to scan SSH service are
    - ssh2-enum-algos.nse
    - ssh-auth-methods.nse
    - ssh-brute.nse
    - ssh-hostkey.nse
    - ssh-publickey-acceptance.nse
    - ssh-run.nse
    - sshv1.nse 
### Usage
```
# executing ssh2-enum-algos.nse script on target IP address
nmap -A -vv -sV -p 22 --script=ssh2-enum-algos <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt

# executing ssh-auth-methods.nse script on target IP address
nmap -A -vv -sV -p 22 --script=ssh-auth-methods <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt

# executing ssh-brute.nse script on target IP address
nmap -A -vv -sV -p 22 --script=ssh-brute <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt

# executing ssh-brute.nse script with username list and password list on target IP address
nmap -A -vv -sV -p 22 --script=ssh-brute --script-args userdb=users.lst,passdb=pass.lst \ --script-args ssh-brute.timeout=4s <ip_address>

# executing ssh-hostkey.nse script on target IP address
nmap -A -vv -sV -p 22 --script=ssh-hostkey <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt

# executing publickey-acceptance.nse script on target IP address
nmap -A -vv -sV -p 22 --script=publickey-acceptance <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt

# executing ssh-run.nse script on target IP address
nmap -A -vv -sV -p 22 --script=ssh-run <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt

# executing sshvi.nse script on target IP address
nmap -A -vv -sV -p 22 --script=sshv1 <ip_address> -oX yyyy-mm-dd-nmap_scan_reports.xml | tee -a yyyy-mm-dd-nmap_scan_reports.txt
```

### ssh_scan
* The ssh_scan is a free and opensource application. It is a prototype SSH configuration and policy scanner for Linux 
  and UNIX servers. It scans the destination host and tells a list of configured options.
* It also recommends possible policy, algorithms and configuration parameters such as KexAlgorithms, Ciphers, MACs etc.
* Some of the key benefits are
    - It uses native Ruby and BinData to scan the system and requires very minimal dependencies.
    - It point at an SSH service and get a JSON report.
    - It is highly configurable.
* The syntax is : `ssh_scan [options]` where

 | Option                                                 | Meaning                                                               |
 |--------------------------------------------------------|-----------------------------------------------------------------------|
 | -t, --target [IP/Range/Hostname]                       | IP/Ranges/Hostname to scan                                            |
 | -f, --file [FilePath]                                  | File Path of the file containing IP/Range/Hostnames to scan           |
 | -T, --timeout [seconds]                                | Timeout per connect after which ssh_scan gives up on the host         |
 | -L, --logger [Log File Path]                           | Enable logger                                                         |
 | -O, --from_json [FilePath]                             | File to read JSON output from                                         |
 | -o, --output [FilePath]                                | File to write JSON output to                                          |
 | --output-type [json, yaml]                             | Format to write stdout to json or yaml                                |
 | -p, --port [PORT]                                      | Port (Default: 22)                                                    |
 | -P, --policy [FILE]                                    | Custom policy file (Default: Mozilla Modern)                          |
 | --threads [NUMBER]                                     | Number of worker threads (Default: 5)                                 |
 | --fingerprint-db [FILE]                                | File location of fingerprint database (Default: ./fingerprints.db)    |
 | --suppress-update-status                               | Do not check for updates                                              |
 | -u, --unit-test [FILE]                                 | Throw appropriate exit codes based on compliance status               |
 | -V [STD_LOGGING_LEVEL], --verbosity <br> -v, --version | Display just version info                                             |
 | -h, --help                                             | Show this message                                                     |
 ----------------------------------------------------------------------------------------------------------------------------------
    
 ### Usage
```
# ssh_scan on a target IP
ssh_scan -t 192.168.1.1

# ssh_scan on target host
ssh_scan -t server.example.com

# ssh_scan on loopback ipv6 address
ssh_scan -t ::1

# ssh_scan on loopback ipv6 address and timeout after 5 seconds
ssh_scan -t ::1 -T 5

# ssh_scan on given list of IP addresses
ssh_scan -f hosts.txt

# to output scan result on json format
ssh_scan -o output.json

# To read json output from a file and then to write it on another file
ssh_scan -O output.json -o rescan_output.json

# ssh_scan on a given IP address and given port number
ssh_scan -t 192.168.1.1 -p 22222

# ssh_scan on a given IP address and given port number. Log the version information to a file.
ssh_scan -t 192.168.1.1 -p 22222 -L output.log -V INFO

# ssh_scan on given IP address based on given policy file
ssh_scan -t 192.168.1.1 -P custom_policy.yml

# ssh_scan on target IP address. Throw exit codes based on compliance status
ssh_scan -t 192.168.1.1 --unit-test -P custom_policy.yml
```

### ssh-audit
* SSH Audit is a Python based tool for information gathering and auditing SSH services.
* It can fingerprint services based on the presence of supported features and server banners. 
* Also gives recommendations to help improve server's security. 
* It is an excellent tool for checking the security of SSH services.
* Some of the features are
    - Test for SSH1 and SSH2 protocol server support
    - It can grab banner, recognize device, operating system and compressions.
    - It gathers key-exchange, host-key, encryption and message authentication code algorithms.
    - It provides algorithm information such as : available since, removed/disabled, unsafe/weak/legacy etc.
    - It provides algorithm recommendations such as : append or remove based on recognised software version.
    - Output security information such as issues, CVE lists etc.
    - Provides historical information.
    - No dependencies, compatible with Python2.6+, Python3.x and PyPy
* The syntax is `ssh-audit.py [-1246pbnvl] host_name` where 

 | Option                  | Meaning                                        |
 |-------------------------|------------------------------------------------|
 | -1,  --ssh1             | force ssh version 1 only                       |
 | -2,  --ssh2             | force ssh version 2 only                       |
 | -4,  --ipv4             | enable IPv4 (order of precedence)              |
 | -6,  --ipv6             | enable IPv6 (order of precedence)              |
 | -p,  --port=<port>      | port to connect                                |
 | -b,  --batch            | batch output                                   |
 | -n,  --no-colors        | disable colors                                 |
 | -v,  --verbose          | verbose output                                 |
 | -l,  --level=<level>    | minimum output level (info or warn or fail)    |
 ---------------------------------------------------------------------------

### Usage
```
# executing ssh-audit.py script on host www.example_host.com
./ssh-audit.py www.example_host.com | tee -a host-yyyy-mm-dd-ssh-audit_reports.txt

# executing ssh-audit.py script with sshv1 and sshv2 scan on target host www.example_host.com
./ssh-audit.py -1 -2 -vv www.example_host.com | tee -a host-yyyy-mm-dd-ssh-audit_reports.txt
```
