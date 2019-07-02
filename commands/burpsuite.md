# Description: Burpsuite

### References
*   [Penetration Testing with Burpsuite](https://portswigger.net/burp/documentation/desktop/penetration-testing) <br>
        - [Using the Target tool](https://portswigger.net/burp/documentation/desktop/tools/target/using) <br>
        - [Using Burp Proxy](https://portswigger.net/burp/documentation/desktop/tools/proxy/using)<br>
        - [Using Burp Intruder](https://portswigger.net/burp/documentation/desktop/tools/intruder/using) <br> 
        - [Using Burp Repeater](https://portswigger.net/burp/documentation/desktop/tools/repeater/using) <br>
*   [Burpsuite Scanner](https://portswigger.net/burp/documentation/desktop/scanning)
*   [Burpsuite Guide](https://www.kalitut.com/2019/05/burp-suite.html)
*   [A Basic Tutorial](https://resources.infosecinstitute.com/burpsuite-tutorial/#gref)

### Introduction
* Burp Suite is a Java based web penetration testing framework. 
* It helps to identify vulnerabilities and verify attack vectors that are affecting web applications. 
* Burp Suite can be classified as an Interception Proxy. While browsing the target application, it allows the tester to 
  configure the internet browser to route traffic through the Burp Suite proxy server. 
* Burp Suite then acts as a (sort of) Man In The Middle by capturing and analysing each request to and from the target 
  web application so that they can be analysed. Later it allows tester to pause, manipulate and replay individual HTTP 
  requests in order to analyse potential parameters or injection points. 
* Injection points can be specified for manual as well as automated fuzzing attacks to discover potentially unintended 
  application behaviours, crashes and error messages. 
* At high level, Burp Suite is used to
     - Scan for vulnerabilities
     - Intercept browser traffic
     - Automate custom attacks
     - Perform manual testing using a variety of tools
* The tools offered as a part of Burp Suite are 

| Burp tools           |       Purpose                                 |
|----------------------|-----------------------------------------------|
| HTTP proxy           |   Burp proxy captures the cookie details and HTTP headers of the page |
| Scanner              |   Used to automatically scan websites for content and security vulnerabilities  |
| Intruder             |   It allows to perform customized automated attacks, to carry out all kinds of testing tasks |
| Spider               |   Used for spidering/crawling a give scope of pages |
| Repeater             |   Used for manipulating and resending individual requests |
| Comparer             |   Used to perform a visual comparision of bits of application data to find interesting differences |
| Decoder              |   Lets to transform bits of application data using common encoding and decoding schemes   |
| Extender             |   Allowing to easily write own plugins, to perform complex and highly customized tasks within Burp |
| Sequencer            |   Used to analyze the quality of randomness in an application's session tokens    |
 
### Usage
* Burp is designed to be used alongside with browser. Burp functions as an HTTP proxy server, and all the HTTP or HTTPS 
  traffic from browser passe through Burp.
* Confirm if Burp's Proxy listener is active and working: `Goto Proxy tab => Options => look in Proxy listeners 
  section.` The 'Running' column should be checked with interface set as 127.0.0.1:8080.
* Configure the browser to use the Burp Proxy listener as its HTTP proxy server. Change browser's proxy settings to use 
  the proxy host address 127.0.0.1 and port 8080 for both http and https protocols.
* After configuring check by opening a HTTP website => Open Burp => go to Proxy tab => click 'Intercept is off' to 
  switch it on.
* After a while switch it off. After interception is off the 'http' website will get loaded to browser.
* To configure browser to be able to send HTTPS requests through Burp, requires to install Burp's Certificate Authority 
  (CA) SSL certificate in browser's trust store, otherwise it will flash security warning. 
  [Guide to installing Burp's Certificate Authority (CA) SSL certificate](https://support.portswigger.net/customer/portal/articles/1783075-installing-burp-s-ca-certificate-in-your-browser)
* Each HTTP request made by browser is displayed in the intercept tab. Each message can be viewed and edited if required.
* Any of the captured request can be selected and sent to various Burp tools such as spider, scanner, intruder, 
  repeater, sequencer, Heartbleed test etc.
* Forward button is used to send the request to the destination web server.
* If at any time any intercepted messages is pending, it needs to be forwarded in order to complete loading of pages in 
  the browser.
* The Proxy history keeps a record of all requests and responses.
* Burp's Target menu maintains a sitemap of all the URL's that was visited in the browser.
* Burpsuite Configuration Options

|   Option                  |       Meaning         |
|---------------------------|-----------------------|
|   Display                 |   Configure the font and character set used to display HTTP messages. |
|   Target Scope            |   It tells Burp the items that are willing to be attacked. |
|   Platform authentication |   If application server employs any platform level (HTTP) authentication, Burp can be configured to handle authentication automatically. |
|   Session handling        |   Situations such as reactive session termination, use of pre-request tokens etc hinder automated or manual testing. Burp can handle such situations using a combination of session handling rules and macros. |
|   Task scheduling         |   Burp can be configured to schedule tasks at given times or intervals.    |
