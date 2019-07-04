# Description : Directory Search

### References
- [DirSearch: A Quick Guide](https://securityonline.info/dirsearch-https-directoryfile-brute-forcer/) 

### Introduction
* Directory Search is a form of conducting a brute force test, to find out hidden fies and directories inside a web 
  server for penetration testing.
* Path Traversal or Directory Traversal
    * It may be possible to access arbitrary files and directories stored on file system including application source 
      code or configuration and critical system files by manipulating variables.
    * A path traversal attack or directory traversal attack aims to access files and directories that are stored outside 
      the web root folder.
* Any of the following tools cab be used to perform directory traversal test :
    - DirSearch
    - WFuzz
    - Dirb
* DirSearch is a command line-based tool, used to brute force any web directory based on wordlist. 
* It will make an http request and see the http response code of each request. 
* DirSearch doesn't look for vulnerabilities but it looks for the web contents that can be vulnerable. 

### Usage

* The general syntax is `dirsearch.py [-u|--url] target [-e|--extensions] extensions [options]`.
* The options along with their meaning


 | Option                                                              | Meaning                                                                                            |
 |---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
 | -u URL or --url=URL                                                 | URL target                                                                                         |
 | -L URLLIST or --url-list=URLLIST                                    | URL list target                                                                                    |
 | -e EXTENSIONS or --extensions=EXTENSIONS                            | Extension list separated by comma (Example: php,asp)                                               |
 | -w WORDLIST or --wordlist=WORDLIST                                  | Input a wordlist                                                                                   |
 | -l or --lowercase                                                   | To force lowercase search                                                                          |     
 | -f or --force-extensions                                            | Force extensions for every wordlist entry                                                          |
 | -s DELAY or --delay=DELAY                                           | Delay between requests (float number)                                                              |
 | -r or --recursive                                                   | Bruteforce recursively                                                                             |
 | -R RECURSIVE_LEVEL_MAX or --recursive-level-max=RECURSIVE_LEVEL_MAX | Max recursion level (subdirs) (Default: 1 [only rootdir + 1 dir])                                  |
 | --suppress-empty or --suppress-empty                                | To suppress empty lines                                                                            |
 | --scan-subdir=SCANSUBDIRS or --scan-subdirs=SCANSUBDIRS             | Scan subdirectories of the given -u or --url (separated by comma)                                  |
 | --exclude-subdir=EXCLUDESUBDIRS or --exclude-subdirs=EXCLUDESUBDIRS | Exclude the following subdirectories during recursive scan (separated by comma)                    |
 | -t THREADSCOUNT or --threads=THREADSCOUNT                           | Number of Threads                                                                                  |
 | -x EXCLUDESTATUSCODES or --exclude-status=EXCLUDESTATUSCODES        | Exclude status code, separated by comma (example: 301,500)                                         |
 | -c COOKIE or --cookie=COOKIE                                        | To set cookie information                                                                          |
 | --ua=USERAGENT or --user-agent=USERAGENT                            | To specify useragent                                                                               |
 | -F or --follow-redirects                                            | To follow if any redirection happens |                                                             |
 | -H HEADERS or --header=HEADERS                                      | Headers to add (example: --header "Referer: example.com" --header "User-Agent: IE"                 |
 | --random-agents or --random-user-agents                             | To automatically change the user agent after specified period of time to a randomly selected one   |                                                      |
 | --timeout=TIMEOUT                                                   | Connection timeout                                                                                 |
 | --ip=IP                                                             | Resolve name to IP address                                                                         |
 | --proxy=HTTPPROXY or --http-proxy=HTTPPROXY                         | Http Proxy (example: localhost:8080                                                                |
 | --http-method=HTTPMETHOD                                            | Method to use, default: GET, possible also: HEAD;POST                                              |
 | --max-retries=MAXRETRIES                                            | To set maximun number of retries                                                                   |                                  
 | -b or --request-by-hostname                                         | By default dirsearch will request by IP for speed. This forces requests by hostname                |
 | --simple-report=SIMPLEOUTPUTFILE                                    | Only found paths                                                                                   |
 | --plain-text-report=PLAINTEXTOUTPUTFILE                             | Found paths with status codes                                                                      |
 | --json-report=JSONOUTPUTFILE                                        | To get output report in JSON format                                                                |
 ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Usage
```
# executing dirsearch.py on target IP, with extension search set as 'php files', and forcing to exclude status certain codes
./dirsearch.py –u http://192.18.1.5/dvwa -e php -f -x 400,403,404

# executing dirsearch.py on target host, with extension search set as 'aspx files and php files'
./dirsearch.py -u google.com -e aspx,php
```
