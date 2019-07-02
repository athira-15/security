# Description : SSL Security Testing 

### References
* [About SSL Cryptography](https://www.digicert.com/ssl-cryptography.htm)
* [The sslscan](https://chousensha.github.io/blog/2017/06/24/sslscan-kali-linux-tools/)
* [Nmap : ssl-enum-ciphers.nse](https://nmap.org/nsedoc/scripts/ssl-enum-ciphers.html)
* [Nmap : ssl-cert.nse](https://nmap.org/nsedoc/scripts/ssl-cert.html)
* [Installation : testssl.sh ](https://github.com/drwetter/testssl.sh/)
* [Examples : testssl.sh](https://www.tecmint.com/testssl-sh-test-tls-ssl-encryption-in-linux-commandline/)

### Introduction
* Secured Sockets Layer (SSL) is a protocol developed by Netscape for transmitting private documents via Internet in a 
  secured form. SSL uses a cryptographic system that uses two keys to encrypt data.
* A public key known to everyone and a private key or secret key known only to the recipient of the message.
* SSL protocol is typically used when a web browser needs to securely connect to a web server over the inherently 
  insecure Internet.URLs that require an SSL connection start with https instead of http.
* How SSL Works 
    - The handshake between client and server can be summed up into three main phases namely Hello, CertificateExchange 
      and KeyExchange.
    - Hello
        - The handshake begins with the client sending a CilenHello message. 
        - It contains all the information the server needs in order to connect to the client via SSL such as: various 
          cipher suites and maximum SSL version supported by client.
        - Similarly server responds with ServerHello, which contains similar information required by client.
    - CertificateExchange
        - After establishing a contact, server proves its identity by using its SSL certificate. An SSL certificate 
          contains information such as name of owner, domain, certificate's public key, certificate's validity dates etc.
        - The client checks that it is verified and trusted by any one of the Certificate Authorities (CA).
    - KeyExchange
        - PKI (Public Key Infrastructure) is what binds keys with user identities by means of Certificate Authority. 
          PKI use a hybrid cryptosystem and benefits from using both types of encryptio. In SSL communications, the 
          server's SSL Certificate contains an asymmetric public and private key pairs. The session key that the server 
          and the browser create during the SSL. 
    - Handshake is symmetric. It can be summed up as
        * Server sends a copy of its asymmetric public key.
        * Browser creates a symmetric session key and encrypts it with the server's asymmetric public key. Then sends it 
          to the server.
        * Server decrypts the encrypted session key using its asymmetric private key to get the symmetric session key.
        * Server and Browser now encrypt and decrypt all transmitted data with the symmetric session key. This allows 
          for a secure channel because only the browser and the server know the symmetric session key, and the session 
          key is only used for that session. If the browser was to connect to the same server the next day, a new 
          session key would be created. 
* SSL Security Testing Methodologies
    - sslscan
    - Nmap NSE Scripts for SSL
    - testssl.sh script
    
### sslscan
* It is a fast SSL/TLS scanner that queries SSL/TLS services, such as HTTPS, in order to determine the ciphers that are 
  supported. It is designed to be easy, lean and fast. 
* The output includes preferred ciphers of the SSL/TLS service. 
* The general syntax is `sslscan [Options] [host:port | host]` where

| Options                       |           Meaning             |
|-------------------------------|--------------------------------|
|  --targets=<file>             |       A file containing a list of hosts to check. Hosts can  be supplied  with ports (host:port) |
|  --sni-name=<name>            |       Hostname for SNI    |
|  --ipv4, -4                   |       Only use IPv4   |
|  --ipv6, -6                   |       Only use IPv6   |
|  --show-certificate           |       Show full certificate information   |
|  --no-check-certificate       |       Don't warn about weak certificate algorithm or keys |
|  --show-client-cas            |       Show trusted CAs for TLS client auth    |
|  --show-ciphers               |       Show supported client ciphers   |
|  --show-cipher-ids            |       Show cipher ids |
|  --show-times                 |       Show handhake times in milliseconds |
|  --ssl2                       |       Only check SSLv2 ciphers    |
|  --ssl3                       |       Only check SSLv3 ciphers    |
|  --tls10                      |       Only check TLSv1.0 ciphers  |
|  --tls11                      |       Only check TLSv1.1 ciphers  |
|  --tls12                      |       Only check TLSv1.2 ciphers  |
|  --tlsall                     |       Only check TLS ciphers (all versions)   |
|  --ocsp                       |       Request OCSP response from server   |
|  --pk=<file>                  |       A file containing the private key or a PKCS#12 file containing a private key/certificate pair |
|  --pkpass=<password>          |       The password for the private  key or PKCS#12 file |
|  --certs=<file>               |       A file containing PEM/ASN1 formatted client certificates |
|  --no-ciphersuites            |       Do not check for supported ciphersuites |
|  --no-fallback                |       Do not check for TLS Fallback SCSV |
|  --no-renegotiation           |       Do not check for TLS renegotiation |
|  --no-compression             |       Do not check for TLS compression (CRIME) |
|  --no-heartbleed              |       Do not check for OpenSSL Heartbleed (CVE-2014-0160) |
|  --starttls-ftp               |       STARTTLS setup for FTP  |
|  --starttls-imap              |       STARTTLS setup for IMAP |
|  --starttls-irc               |       STARTTLS setup for IRC  |
|  --starttls-ldap              |       STARTTLS setup for LDAP |
|  --starttls-pop3              |       STARTTLS setup for POP3 |
|  --starttls-smtp              |       STARTTLS setup for SMTP |
|  --starttls-mysql             |       STARTTLS setup for MYSQL    |
|  --starttls-xmpp              |       STARTTLS setup for XMPP |
|  --starttls-psql              |       STARTTLS setup for PostgreSQL   |
|  --xmpp-server                |       Use a server-to-server XMPP handshake   |
|  --http                       |       Test a HTTP connection  |
|  --rdp                        |       Send RDP preamble before starting scan  |
|  --bugs                       |       Enable SSL implementation bug work-arounds  |
|  --timeout=<sec>              |       Set socket timeout. Default is 3s   |
|  --sleep=<msec>               |       Pause between connection request. Default is disabled   |
|  --xml=<file>                 |       Output results to an XML file, <file> can be -, which means stdout  |
|  --version                    |       Display the program version |
|  --verbose                    |       Display verbose output  |
|  --no-cipher-details          |       Disable EC curve names and EDH/RSA key lengths output   |
|  --no-colour                  |       Disable coloured output |
|  --help                       |       Display the  help text  you are  now reading    |
------------------------------------------------------------------------------------------------------------------------
* Usage
```
sslscan 127.0.0.1
sslscan https://www.examplehost.com
sslscan --ssl2 --ssl3 --show-ciphers --verbose --http <ip_address>
```

### Nmap NSE Scripts for SSL
* The Nmap Scripting Engine (NSE) is one of Nmap's most powerful and flexible features. 
* These scripts are written in Lua programming language. NSE scripts helps to automate a wide variety of networking 
  tasks. 
* NSE scripts available in Nmap to scan SSL service are
    - ssl-ccs-injection.nse
    - ssl-cert-intaddr.nse
    - ssl-cert.nse
    - ssl-date.nse
    - ssl-dh-params.nse
    - ssl-enum-ciphers.nse
    - ssl-heartbleed.nse
    - ssl-known-key.nse
    - ssl-poodle.nse
    - sslv2-drown.nse
    - sslv2.nse
    - sstp-discover.nse 

### Usage
```
nmap -sV --script ssl-enum-ciphers -p 443 <ip_address>

nmap -sV -sC <ip_address>

nmap --script ssl-enum-ciphers -p 443 www.examplehost.com
```

### testssl.sh script
* testssl.sh is a free command line tool that checks a server's service on any port for the support of TLS/SSL ciphers, 
  protocols as well as some cryptographic flaws.
* Some of its features includes
    - Easy to install and use. Produces clear output.
    - Highly flexible, can be used to check any SSL/TLS enabled services.
    - Perform a general check or single checks.
    - Comes with various command line options.
    - Supports different output types, including colored output.
    - Supports SSL Session ID check.
    - Offers absolute privacy.
    - Supports checking for multiple server certificates.
* The general syntax is `testssl.sh [OPTIONS] <URI> or testssl.sh [OPTIONS] --file <FILE>` where

| Option                                                |           Meaning                                                     |
|-------------------------------------------------------|-----------------------------------------------------------------------|
|   --help                                              |    what you're looking at |
|     -b, --banner                                      |    displays banner + version of testssl.sh |
|     -v, --version                                     |    same as previous | 
|     -V, --local                                       |    pretty print all local ciphers |
|     -V, --local <pattern>                             |    which local ciphers with <pattern> are available? If pattern is not a number: word match |
|     <pattern>                                         |    is always an ignore case word pattern of cipher hexcode or any other string in the name, kx or bits |
| "testssl.sh <URI>", where <URI> is:                   |    <URI> host or host:port or URL or URL:port , port 443 is default, URL can only contain HTTPS protocol) |
| "testssl.sh [options] <URI>", where [options] is:     |    -t, --starttls <protocol> Does a default run against a STARTTLS enabled <protocol, protocol is <ftp or smtp or lmtp or pop3 or imap or xmpp or telnet or ldap or nntp or postgres or mysql> |
| --xmpphost <to_domain>                                |    For STARTTLS enabled XMPP it supplies the XML stream to-'' domain -- sometimes needed
|     --mx <domain/host>                                |    Tests MX records from high to low priority (STARTTLS, port 25)
|     --file/-iL <fname>                                |    Mass testing option: Reads one testssl.sh command line per line from <fname>. <br> Implicitly turns on "--warnings batch". Can be combined with --serial or --parallel. <br> Text format 1: Comments via # allowed, EOF signals end of <fname>. <br> Text format 2: nmap output in greppable format (-oG), 1 port per line allowed. |
|     --mode <serial or parallel>                       |    Mass testing to be done serial (default) or parallel (--parallel is shortcut for the latter) 
|   Note : <br>single check as <options> ("testssl.sh URI" does everything except -E and -g):  |
|   -e, --each-cipher                                   |    checks each local cipher remotely |
|    -E, --cipher-per-proto                             |    checks those per protocol |
|    -s, --std, --standard                              |    tests certain lists of cipher suites by strength |
|     -p, --protocols                                   |    checks TLS/SSL protocols (including SPDY/HTTP2) |
|     -g, --grease                                      |    tests several server implementation bugs like GREASE and size limitations |
|     -S, --server-defaults                             |    displays the server's default picks and certificate info |
|     -P, --server-preference                           |    displays the server's picks: protocol+cipher |
|     -x, --single-cipher <pattern>                     |    tests matched <pattern> of ciphers (if <pattern> not a number: word match) |
|     -c, --client-simulation                           |    test client simulations, see which client negotiates with cipher and protocol |
|     -h, --header, --headers                           |    tests HSTS, HPKP, server/app banner, security headers, cookie, reverse proxy, IPv4 address |
|     -U, --vulnerable                                  |    tests all (of the following) vulnerabilities (if applicable) |
|     -H, --heartbleed                                  |    tests for Heartbleed vulnerability |
|     -I, --ccs, --ccs-injection                        |    tests for CCS injection vulnerability |
|     -T, --ticketbleed                                 |    tests for Ticketbleed vulnerability in BigIP loadbalancers |
|     -BB, --robot                                      |    tests for Return of Bleichenbacher's Oracle Threat (ROBOT) vulnerability |
|     -R, --renegotiation                               |    tests for renegotiation vulnerabilities |
|     -C, --compression, --crime                        |    tests for CRIME vulnerability (TLS compression issue) |
|     -B, --breach                                      |    tests for BREACH vulnerability (HTTP compression issue) |
|     -O, --poodle                                      |    tests for POODLE (SSL) vulnerability |
|     -Z, --tls-fallback                                |    checks TLS_FALLBACK_SCSV mitigation |
|     -W, --sweet32                                     |    tests 64 bit block ciphers (3DES, RC2 and IDEA): SWEET32 vulnerability |
|     -A, --beast                                       |    tests for BEAST vulnerability |
|     -L, --lucky13                                     |    tests for LUCKY13 |
|     -F, --freak                                       |    tests for FREAK vulnerability |
|     -J, --logjam                                      |    tests for LOGJAM vulnerability |
|     -D, --drown                                       |    tests for DROWN vulnerability |
|     -f, --pfs, --fs, --nsa                            |    checks (perfect) forward secrecy settings |
|     -4, --rc4, --appelbaum                            |    which RC4 ciphers are being offered? |
|Note : <br>tuning / connect options (most also can be preset via environment variables): |    
|     --fast                                            |    omits some checks: using openssl for all ciphers (-e), show only first preferred cipher. |
|     -9, --full                                        |    includes tests for implementation bugs and cipher per protocol (could disappear) |
|     --bugs                                            |    enables the "-bugs" option of s_client, needed e.g. for some buggy F5s |
|     --assume-http                                     |    if protocol check fails it assumes HTTP protocol and enforces HTTP checks |
|     --ssl-native                                      |    fallback to checks with OpenSSL where sockets are normally used |
|     --openssl <PATH>                                  |    use this openssl binary (default: look in $PATH, $RUN_DIR of testssl.sh) |
|     --proxy <host:port or auto>                       |    (experimental) proxy connects via <host:port>, auto: values from $env ($http(s)_proxy) |
|     -6                                                |    also use IPv6. Works only with supporting OpenSSL version and IPv6 connectivity |
|     --ip <ip>                                         |    a) tests the supplied <ip> v4 or v6 address instead of resolving host(s) in URI<br> b) arg "one" means: just test the first DNS returns (useful for multiple IPs) |
|     -n, --nodns <min or none>                         |    if "none": do not try any DNS lookups, "min" queries A, AAAA and MX records |
|     --sneaky                                          |    leave less traces in target logs: user agent, referer |
|     --ids-friendly                                    |    skips a few vulnerability checks which may cause IDSs to block the scanning IP |
|     --phone-out                                       |    allow to contact external servers for CRL download and querying OCSP responder |
|     --add-ca <cafile>                                 |    path to <cafile> or a comma separated list of CA files enables test against additional CAs. |
|Note : <br> output options (can also be preset via environment variables):     |
|     --warnings <batch or off or false>                |    "batch" doesn't ask for a confirmation, "off" or "false" skips connection warnings |
|     --openssl-timeout <seconds>                       |    useful to avoid hangers. <seconds> to wait before openssl connect will be terminated |
|     --quiet                                           |    don't output the banner. By doing this you acknowledge usage terms normally appearing in the banner |
|     --wide                                            |    wide output for tests like RC4, BEAST. PFS also with hexcode, kx, strength, RFC name |
|     --show-each                                       |    for wide outputs: display all ciphers tested -- not only succeeded ones |
|     --mapping <openssl or iana or rfc or no-openssl or no-iana or no-rfc  | openssl: use the OpenSSL cipher suite name as the primary name cipher suite name form (default)<br> iana or rfc -> use the IANA/(RFC) cipher suite name as the primary name cipher suite name form <br> no-openssl -> don't display the OpenSSL cipher suite name, display IANA/(RFC) names only<br> no-iana or no-rfc -> don't display the IANA/(RFC) cipher suite name, display OpenSSL names only |
|    --color <0 or 1 or 2 or 3>                         |    0: no escape or other codes,  1: b/w escape codes,  2: color (default), 3: extra color (color all ciphers) |
|     --colorblind                                      |    swap green and blue in the output |
|     --debug <0-6>                                     |    1: screen output normal but keeps debug output in /tmp/.  2-6: see "grep -A 5 '^DEBUG=' testssl.sh" |
| Note: <br> file output options (can also be preset via environment variables) |
|     --log, --logging                                  |    logs stdout to '${NODE}-p${port}${YYYYMMDD-HHMM}.log' in current working directory (cwd) |
|     --logfile or -oL <logfile>                           |    logs stdout to 'dir/${NODE}-p${port}${YYYYMMDD-HHMM}.log'. If 'logfile' is a dir or to a specified 'logfile' |
|     --json                                            |    additional output of findings to flat JSON file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd |
|     --jsonfile or -oj <jsonfile>                      |    additional output to the specified flat JSON file or directory, similar to --logfile |
|     --json-pretty                                     |    additional JSON structured output of findings to a file '${NODE}-p${port}${YYYYMMDD-HHMM}.json' in cwd |
|     --jsonfile-pretty or -oJ <jsonfile>               |    additional JSON structured output to the specified file or directory, similar to --logfile |
|     --csv                                             |    additional output of findings to CSV file '${NODE}-p${port}${YYYYMMDD-HHMM}.csv' in cwd or directory |
|     --csvfile or -oC <csvfile>                        |    additional output as CSV to the specified file or directory, similar to --logfile |
|     --html                                            |    additional output as HTML to file '${NODE}-p${port}${YYYYMMDD-HHMM}.html' |
|     --htmlfile or -oH <htmlfile>                      |    additional output as HTML to the specified file or directory, similar to --logfile |
|     --out(f,F)ile or -oa/-oA <fname>                  |    log to a LOG,JSON,CSV,HTML file (see nmap). -oA/-oa: pretty/flat JSON. "auto" uses '${NODE}-p${port}${YYYYMMDD-HHMM}' |
|     --hints                                           |    additional hints to findings |
|     --severity <severity>                             |    severities with lower level will be filtered for CSV+JSON, possible values <LOW or MEDIUM or HIGH or CRITICAL> |
|     --append                                          |    if (non-empty) <logfile>, <csvfile>, <jsonfile> or <htmlfile> exists, append to file. Omits any header |
|    --outprefix <fname_prefix>                         |    before  '${NODE}.' above prepend <fname_prefix> |
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
* Usage
``` 

testssl.sh www.examplehost.com

testssl.sh --ip=one --wide https://testssl.net:443

testssl.sh -t smtp smtp.gmail.com:25

testssl.sh --starttls=imap imap.gmx.net:143
```
