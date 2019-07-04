# Description: Skipfish

### References
* [Skipfish : How to use](https://github.com/spinkham/skipfish/wiki/How-To-Use)  
* [Understanding and Using Skipfish](https://lcamtuf.blogspot.com/2010/11/understanding-and-using-skipfish.html)
* [Skipfish : General Introduction and Installation](https://www.mamunahmed.com/02/run-skipfish-using-ubuntu-10-04-lucid-lynx-to-test-your-website-security/)

### Introduction
* Skipfish is an active web application security reconnaissance tool. It prepares an interactive sitemap for the target 
  site by carrying out recursive crawl and dictionary-based probes. 
* The resulting map is then annotated with the output from several active security checks. It is a very fast scanner 
  that help to identify vulnerabilities such as
    - Cross-Site Scripting
    - SQL injection
    - Command injection
    - XML/XPath injection
    - Directory traversal and file inclusions
    - Directory listing
* Main features are
    - Automatic word list construction based on site content analysis
    - Heuristic recognition of obscure path and query-based parameters handling schemes
    - Snort style content signatures which will highlight server errors, information leaks or potentially dangerous web 
      applications
    - Bundled security checks are designed to handle tricky scenarios such as: stored XSS, blind SQL or XML injection or 
      blind shell injection
* The general syntax is `skipfish [ options ... ] -W wordlist -o output_dir start_url [ start_url2 ... ]`
* The various options are 

 | Category                     | Option                                                                                                                                                                                                            | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
 |------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
 | Authentication and access    | 1. -A user:pass<br>2. -F host=IP<br>3. -C name=val<br>4. -H name=val<br>5. -b (i or for p)<br>6. -N                                                                                                               | 1. use specified HTTP authentication credentials<br>2. pretend that 'host'  resolves to 'IP'<br>3. append a custom cookie to all requests<br>4. append a custom HTTP header to all requests<br>5. use headers consistent with MSIE/Firefox/iPhone<br>6. do not accept any new cookies                                                                                                                                                                                                                                                                                                                                                         |
 | Crawl scope                  | 1. -d max_depth<br>2. -c max_child<br>3. -x max_desc<br>4. -r r_imit<br>5. -p crawl%<br>6. -q hex<br>7. -l string<br>8. -X string<br>9. -K string<br>10. -D domain<br>11. -B domain<br>12. -Z<br>13. -O<br>14. -P | 1. maximum crawl tree depth (16)<br>2. maximum children to index per node (512)<br>3. maximum descendants to index per branch (8192)<br>4.  max total number of requests to send (100000000)<br>5.  node and link crawl probability (100%)<br>6.  repeat probabilistic scan with given seed<br>7. only follow URLs matching 'string'<br>8. exclude URLs matching 'string'<br>9. do not fuzz parameters named 'string'<br>10. crawl cross-site links to another domain<br>11. trust, but do not crawl, another domain<br>12. do not descend into 5xx locations<br>13. do not submit any forms<br>14. do not parse HTML, etc, to find new links |
 | Reporting options            | 1. -o dir<br>2. -M<br>3. -E<br>4. -U<br>5. -Q<br>6. -u                                                                                                                                                            | 1.  write output to specified directory (required)<br>2. log warnings about mixed content / non-SSL passwords<br>3. log all caching intent mismatches<br>4. log all external URLs and e-mails seen<br>5. completely suppress duplicate nodes in reports<br>6.  be quiet, disable realtime progress stats                                                                                                                                                                                                                                                                                                                                      |
 | Dictionary management options| 1. -W wordlist<br>2. -S wordlist<br>3. -L <br>4. -Y<br>5. -R age<br>6. -T name=val<br>7. -G max_guess                                                                                                             | 1. use a specified read-write wordlist (required)<br>2. load a supplemental read-only wordlist<br>3. do not auto-learn new keywords for the site<br>4. do not fuzz extensions in directory brute-force<br>5. purge words hit more than 'age'  scans ago<br>6.  add new form auto-fill rule<br>7. maximum number of keyword guesses to keep (256)                                                                                                                                                                                                                                                                                              |
 | Performance settings         | 1. -l max_req<br>2. -g max_conn<br>3. -m host_conn<br>4. -f max_fail<br>5. -t req_tmout<br>6. -w rw_tmout<br>7. -i idle_tmout<br>8. -s s_limit<br>9. -e                                                           | 1. max requests per second (0..000000)<br>2. max simultaneous TCP connections, global (40)<br>3. max simultaneous connections, per target IP (10)<br>4. max number of consecutive HTTP errors (100)<br>5. total request response timeout (20 s)<br>6. individual network I/O timeout (10 s)<br>7. timeout on idle HTTP connections (10 s)<br>8. response size limit (200000 B)<br>9. do not keep binary responses for reporting                                                                                                                                                                                                               |
 | Safety settings              | 1. -k duration<br>2. -l max_req<br>3. --config file                                                                                                                                                               | 1. stop scanning after the given duration h:m:s<br>2. max requests per second<br>3. load the specified configuration file                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Usage
```
# Scan type: quick
skipfish -o output/dir/ http://example.com

# Scan type: extensive bruteforce
skipfish [...other options..] -S dictionaries/complete.wl http://example.com

# Scan type: without bruteforcing
skipfish [...other options..] -LY http://example.com

# Scan type: authenticated (basic)
skipfish [...other options..] -A username:password http://example.com

# Scan type: authenticated (cookie)
skipfish [...other options..] -C jsession=myauthcookiehere -X /logout http://example.com

# Scan type: flaky server
skipfish [...other options..] -l 5 -g 2 -t 30 -i 15 http://example.com
```
