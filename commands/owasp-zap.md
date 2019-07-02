# Description : OWASP-ZAP

### References 
* [ZAP Getting Started](https://github.com/zaproxy/zaproxy/wiki/Downloads)   
* [ZAP Penetration Testing A Simple Tutorial](https://www.toobler.com/zap-penetration-testing-simple-tutorial/) 
* [OWASP-ZAP Introduction](https://resources.infosecinstitute.com/introduction-owasp-zap-web-application-security-assessments/#gref)
* [OWASP-ZAP : Command Line Guide](https://github.com/zaproxy/zap-core-help/wiki/HelpCmdline)

### Introduction
* OWASP-ZAP is easy to use web application penetration testing tool. It allows to do manual or automatic website 
  security checks. 
* OWASP Zed Attack Proxy is a Java-based tool that comes with an intuitive graphical interface, allowing web application 
  security testers to perform fuzzing, scripting, spidering and proxying for web application pen testing. 
* To launch OWASP-ZAP from the terminal use `owasp-zap` command.
* ZAP can scan the target site for vulnerabilities by following the below steps
    - Open the web application to be tested.
    - The ZAP will display the website or application under sites option.
    - ZAP will spider that URL, then perform an active scan and display the results.
* ZAP runs on proxy, therefore to set up the proxy in ZAP and to run an active scan, use the following steps
    - Close all active web browser sessions.
    - Go to ZAP tool => Tools Menu => Options => Local Proxy => Change Address=127.0.0.1 Port=8080
    - Configure the same in browser's network settings as : 
        * Browser => Tools Menu => Options => Advanced tab => Network => Settings => Select Manual Proxy Configuration : HTTP Proxy=127.0.0.1 and Port=8080
    - After configuring proxy, connect to the target application through browser.
    - ZAP's additional features can be accessed through 'right click' menus.
    - Click on HTML => Attack => Active scan, to perform active scan on all the pages and display results.
    - ZAP's session can be saved for further reference.   
    - Reports can be generated in any of the following formats :
        * HTML
        * XML
        * Markdown
        * JSON

### Usage
```
TODO
```