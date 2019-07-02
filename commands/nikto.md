# Description: Nikto 

### References
* [Nikto Command Line Options](https://cirt.net/nikto2-docs/options.html)
* [Nikto Usage](https://cirt.net/nikto2-docs/usage.html)
* [Nikto Web Application Vulnerability Scanner](https://resources.infosecinstitute.com/introduction-nikto-web-application-vulnerability-scanner/#gref)
* [Nikto Tutorial](https://hackertarget.com/nikto-tutorial/)

### Introduction
* Nikto is a web application scanner. It scans a web service and looks for known vulnerabilities. It helps to conduct a 
  quick scan against a web application. 
* The Tuning options in Nikto helps to control the test against a target. Nikto performs over 6000 tests against a 
  website for thousands of possible security issues such as: dangerous files, mis-configured services, vulnerable 
  scripts and other issues. 
* It is open source and structured with plugins that extend the capabilities. These plugins are frequently updated with 
  new security checks.
* Some of the Nikto features includes
    - Report can be saved in HTML,XML and CSV formats
    - It supports SSL
    - Scan multiple ports on the server
    - Find subdomain
    - Apache user enumeration
    - Checks for outdated components
    - Detect parking sites
* The options used in Nikto are

| Option     | Meaning                     |
|-----------------|---------------------------------------------|
| -ask+           | Whether to ask about submitting updates {yes:Ask about each (default), no:Don't ask, don't send, auto:Don't ask, just send |
| -Cgidirs+       | Scan these CGI dirs: "none", "all", or values like "/cgi/ /cgi-a/" |
| -config+        | Use this config file |
| -Display+       | Turn on/off display outputs: <br>1:Show redirects<br>2:Show cookies received<br>3:Show all 200/OK responses<br>4:Show URLs which require authentication<br>D:Debug output<br>E:Display all HTTP errors<br>P:Print progress to STDOUT<br>S:Scrub output of IPs and hostnames<br>V:Verbose output |
| -dbcheck        | Check database and other key files for syntax errors
| -evasion+       | Encoding technique: <br>1:Random URI encoding (non-UTF8)<br>2:Directory self-reference (/./)<br>3:Premature URL ending<br>4:Prepend long random string<br>5:Fake parameter<br>6:TAB as request spacer<br>7:Change the case of the URL<br>8:Use Windows directory separator (\)<br>A:Use a carriage return (0x0d) as a request spacer<br>B:Use binary value 0x0b as a request spacer |
| -Format+        | Save file (-o) format: <br>csv:Comma-separated-value<br>json:JSON Format<br>htm:HTML Format<br>nbe:Nessus NBE format<br>sql:Generic SQL (see docs for schema)<br>txt:Plain text<br>xml:XML Format (if not specified the format will be taken from the file extension passed to -output) |
| -Help           | Extended help information |
| -host+          | Target host/URL |
| -404code        | Ignore these HTTP codes as negative responses (always). Format is "302,301" |
| -404string      | Ignore this string in response body content as negative response (always). Can be a regular expression |
| -id+            | Host authentication to use, format is id:pass or id:pass:realm |
| -key+           | Client certificate key file |
| -list-plugins   | List all available plugins, perform no testing |
| -maxtime+       | Maximum testing time per host (e.g., 1h, 60m, 3600s) |
| -mutate+        | Guess additional file names: <br>1:Test all files with all root directories<br>2:Guess for password file names<br>3:Enumerate user names via Apache (/~user type requests)<br>4:Enumerate user names via cgiwrap (/cgi-bin/cgiwrap/~user type requests)<br>5:Attempt to brute force sub-domain names, assume that the host name is the parent domain<br>6:Attempt to guess directory names from the supplied dictionary file |
| -mutate-options | Provide information for mutates |
| -nointeractive  | Disables interactive features |
| -nolookup       | Disables DNS lookups |
| -nossl          | Disables the use of SSL |
| -no404          | Disables nikto attempting to guess a 404 page |
| -Option         | Over-ride an option in nikto.conf, can be issued multiple times |
| -output+        | Write output to this file ('.' for auto-name) |
| -Pause+         | Pause between tests (seconds, integer or float) |
| -Plugins+       | List of plugins to run (default: ALL) |
| -port+          | Port to use (default 80) |
| -RSAcert+       | Client certificate file |
| -root+          | Prepend root value to all requests, format is /directory |
| -Save           | Save positive responses to this directory ('.' for auto-name) |
| -ssl            | Force ssl mode on port |
| -Tuning+        | Scan tuning: <br>1:Interesting File / Seen in logs<br>2:Misconfiguration / Default File<br>3:Information Disclosure<br>4:Injection (XSS/Script/HTML)<br>5:Remote File Retrieval - Inside Web Root<br>6:Denial of Service<br>7:Remote File Retrieval - Server Wide<br>8:Command Execution / Remote Shell<br>9:SQL Injection<br>0:File Upload<br>a:Authentication Bypass<br>b:Software Identification<br>c:Remote Source Inclusion<br>d:WebService<br>e:Administrative Console<br>x:Reverse Tuning Options (i.e., include all except specified) |
| -timeout+       | Timeout for requests (default 10 seconds) |
| -Userdbs        | Load only user databases, not the standard databases<br>all:Disable standard dbs and load only user dbs<br>tests Disable only db_tests and load udb_tests |
| -useragent      | Over-rides the default useragent |
| -until          | Run until the specified time or duration |
| -update         | Update databases and plugins from CIRT.net |
| -url+           | Target host/URL (alias of -host) |
| -useproxy       | Use the proxy defined in nikto.conf, or argument http://server:port |
| -Version        | Print plugin and database versions |
| -vhost+         |   Virtual host (for Host header), requires a value |

### Usage
```
nikto -Display 1234EP -o report.html -Format htm -Tuning 123bde -host 192.168.0.102


nikto -Display V -o hoopoe-2019-04-10-nikto_output.html -Format htm -Tuning 0 1 2 3 4 6 7 a b c -h 192.168.0.106
```
