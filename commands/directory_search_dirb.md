# Description : Directory Search

### References
- [Dirb : A Quick Introduction](https://medium.com/tech-zoom/dirb-a-web-content-scanner-bc9cba624c86)
- [Dirb : A Comprehensive Guide](https://www.hackingarticles.in/comprehensive-guide-on-dirb-tool/)

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
* Dirb is a web content scanner. It looks for existing or hidden web objects. It basically works by launching a 
  directory-based attack against a web server and analyzing the response.
* It comes with a set of preconfigured attack wordlists for easy usage but can also accept customised wordlist given by 
  users. 
* Dirb is a content scanner, not a vulnerability scanner. Its main purpose is to help in professional web application 
  auditing. Especially in security-related testing. It mainly covers some holes not covered by classic web vulnerability 
  scanners.

### Usage
* The general syntax is `dirb <url_base> [<wordlist_file(s)>] [options]`
* The various options and their meanings are as follows

| Option                        |   Meaning             |
|-------------------------------|---------------------------------------------|
|<url_base>                     | Base URL to scan. (Use -resume for session resuming) |
|<wordlist_file(s)>             | List of wordfiles. (wordfile1,wordfile2,wordfile3...) |
|'n'                            | Go to next directory |
|'q'                            | Stop scan. (Saving state for resume) |
|'r'                            | Remaining scan stats |
|-a <agent_string>              | Specify your custom USER_AGENT |
|-b                             | Use path as is |
|-c <cookie_string>             | Set a cookie for the HTTP request |
|-E <certificate>               | path to the client certificate |
|-f                             | Fine tunning of NOT_FOUND (404) detection |
|-H <header_string>             | Add a custom header to the HTTP request |
|-i                             | Use case-insensitive search |
|-l                             | Print "Location" header when found |
|-N <nf_code>                   | Ignore responses with this HTTP code |
|-o <output_file>               | Save output to disk |
|-p <proxy[:port]>              | Use this proxy. (Default port is 1080) |
|-P <proxy_username:proxy_password> | Proxy Authentication |
|-r                             | Don't search recursively |
|-R                             | Interactive recursion. (Asks for each directory) |
|-S                             | Silent Mode. Don't show tested words. (For dumb terminals) |
|-t                             | Don't force an ending '/' on URLs |
|-u <username:password>         | HTTP Authentication |
|-v                             | Show also NOT_FOUND pages |
|-w                             | Don't stop on WARNING messages |
|-X <extensions> / -x <exts_file>| Append each word with this extensions |
|-z <millisecs>                  | Add a milliseconds delay to not cause excessive Flood |

* Usage
```
# Simple Test
dirb http://url/directory/ 

# Test files with '.html' extension
dirb http://url/ -X .html

# Test with apache.txt wordlist
dirb http://url/ /usr/share/dirb/wordlists/vulns/apache.txt

# Simple Test with SSL
dirb https://secure_url/
```
