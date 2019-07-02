# Description: The hydra Command

### Notes
* Hydra (also known as 'thc-hydra') is an online password attack tool. It brute forces various combinations on live 
  services like ftp, telnet, ssh, http, smb etc.
* The general syntax
    ```
    hydra [[[-l LOGIN|-L FILE] [-p PASS|-P FILE]] | [-C FILE]] [-e nsr] [-o FILE] [-t TASKS] [-M FILE [-T TASKS]] 
         [-w TIME] [-W TIME] [-f] [-s PORT] [-x MIN:MAX:CHARSET] [-c TIME] [-ISOuvVd46] [service://server[:PORT][/OPT]]
    ```
* Various Options

| Option                |   Meaning |
|-----------------------|-------------|
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

### Common Examples
```shell
# Check below
```

### Examples With Details
```shell
# TODO
hydra -l root -P password_worst_password_list_2018.txt mysql://192.168.190.154

# TODO
hydra -L userlist.txt -p one_random_password imap://192.168.0.1/PLAIN

# TODO
hydra -l admin -p password ftp://[192.168.0.0/24]/

# TODO
hydra -L logins.txt -P password.txt -M targets.txt ssh
```

### Cool Tricks
* None

### TODO
* None
