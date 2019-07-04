# Description: Nmap Scanner 

### References
* [Nmap Options Summary](https://nmap.org/book/man-briefoptions.html)
* [Nmap Cheat Sheet : A quick reference guide](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/)
* [A Definitive Guide to Nmap](https://www.comparitech.com/net-admin/the-definitive-guide-to-nmap/)
* [Nmap Basic Tutorial](https://hackertarget.com/nmap-tutorial/)

### Introduction
* Nmap is a powerful tool for discovering information about machines on a network or the Internet. 
* It allows to probe a machine with packets to detect everything from running services and open ports to the operating 
  system and software versions. 
* It helps to secure the network. 
* It helps to ensure that servers are properly configured and don't have any open and unsecured ports. 
* It also reports if firewall is correctly filtering ports that should not be externally accessible.

### Scripts
1. Nmap Scanner

* Script name : `nmap_scanner.sh` 
    * Usage: `bash ${0} </path/to/filename> <option_number> | tee -a scan_result.txt`
    * Input file containing target IP addresses : nmap_scanner_target.in
    * The script can perform the following scans : (default is option 1)
        * Intense Scan and complete NSE Vulnerability Scripts execution.
        * Intense Scan plus UDP
        * Intense Scan, all TCP ports
        * Intense Scan, no ping
        * Ping Scan
        * Quick Scan
        * Quick Scan plus
        * Quick traceroute
        * Regular Scan
        * Slow Comprehensive Scan
        * Check if target vulnerable to OpenSSL Heartbleed bug
        * Check if vsFTPd backdoor is present or not
        * Test for Adobe XML external entity injection vulnerability
        * Whether the server accepts or rejects the repeated SSL/TLS request
	    * Check if host is affected with conficker.c or higher
	    * Check if target machine is vulnerable to samba heap overflow vulnerability
	    * Detect if host is infected with stuxnet vulnerability
	    * Determine if web server is protected by IDS/IPS or WAF
	    * Detect the presence of WAF and its version
	    * Check for memory corruption in the postfix SMTP server
	    * Check if SSL used by host has a matching fingerprint
	    * Check for DoS attack
	    
### Output and Report Generation	    
              
 - The output of the scan can be stored in any of the three possible different formats, namely : </br> 
   * .nmap 
   * .gnmap 
   * .xml 
 - Output file name format : `<server_name-yyyy-mm-dd-nmap_scanner_reports.xml>`
 ````
 - In Kali : 
    * To convert or parse the nmap output from xml to html -
    * Tool or package used : saxonb9-1-0-8j saxon.jar or xsltproc or nmap-bootstrap.xsl 
     
        * saxon.jar usage
          java -jar saxon9.jar -a -s:<server_name-yyyy-mm-dd-nmap_scanner_reports.xml> -o:<server_name-yyyy-mm-dd-nmap_scanner_reports.html>
          Note : where, -a : to apply xml parsing, -s : to specify source xml file, -o : to specify resultant html file
    
        * xsltproc usage
          xsltproc <filename.xml> -o <filename.html>
          Note : where, -o : to specify resultant html file
    
        * nmap-bootstrap.xsl usage
          xsltproc -o filename.html nmap-bootstrap.xsl filename.xml
          Note : where, -o : to specify resultant html file
    
 - In Kali : 
    * To convert from <u><b>html to pdf -
    * Tool used : wkhtmltopdf or CutyCapt
    
    * wkhtmltopdf usage
      wkhtmltopdf -s <A4/letter> -O <landscape/portrait> <server_name-yyyy-mm-dd-nmap_scanner_reports.html> <server_name-yyyy-mm-dd-nmap_scanner_reports.pdf>
      Note : where, -s : size  of pdf file, -O : orientation of pdf file
    
    * cutycapt usage
      cutycapt --url=http://www.example.com/ --out=/path/filename.pdf
      Note : where, --url : to specify source URL, --out : to specify output path and filename
 
 - In Windows : 
    * To convert from html to pdf (for oversize html pages) -
    * Tool name: PDFelement 6 Professional or Win2PDF
     
 - All these reports are available under reports/YYYY/nmap_scanner_reports
````

### Nmap Scan Methodolody Followed

* The Nmap Script written in Shell Script is a collection of all prominent Nmap scan commands for Vulnerability Assessment.
* The script is first executed (with default scan option as ‘1’).
* Open ports and the services running are identified to check for any discovery of vulnerabilities associated with it. 
* Versions of the services identified by Nmap are particularly investigated, to identify any important patch related to it 
  has been released. 
* The necessary CVE details are noted down and included in report.
* Multiple options from Nmap Script are executed to figure out more accurate details about the target.