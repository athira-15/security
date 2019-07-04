# Description: w3af

### References 
* [Web Application Attack and Audit Framework Documentation](https://buildmedia.readthedocs.org/media/pdf/w3af/latest/w3af.pdf)
* [W3af walkthrough and Tutorial](https://resources.infosecinstitute.com/w3af-tutorial/#gref)
* [Running w3af](http://docs.w3af.org/en/latest/basic-ui.html)
* [w3af Basic Tutorial](https://www.hackingarticles.in/w3af-web-application-attack-and-audit-framework-tutorial-part-1/)

### Introduction
* The w3af (Web Application audit and attack framework) is a framework for auditing and exploitation of web 
  applications. 
* It is a Python based open source web application security scanner. 
* It provides preconfigured vulnerability scanner and exploitation tool for web applications in support of standards 
  such as OWASP. 
* It has more than 130 plugins and provides information about security vulnerabilities for use in penetration testing 
  which includes check for SQL injection, cross site scripting, local and remote file inclusion etc. <br>
* It offers a graphical user interface and a command-line interface. 
* Some of the major features are as follows :
    - It has a plugin that communicates with each other.
    - It removes some of the headaches involved in manual web application testing.
    - It also has features to exploit the vulnerabilities that it finds.
* From the command line prompt the framework and the plugin settings can be configured, scans can be launched and a 
  vulnerability can be tested for exploitation.
* Following are the configuration options available in w3af command line console:

 | Option            | Meaning                                                                               |
 |-------------------|---------------------------------------------------------------------------------------|
 | start             | Start the scan                                                                        |                                                                                                           
 | plugins           | Enable and configure plugins.                                                         |                                                                                            
 | exploit           | Exploit the vulnerability.                                                            |                                                                                          
 | profiles          | List and use scan profiles.                                                           |                                                                                           
 | cleanup           | Cleanup before starting a new scan.                                                   |                                                                                     
 | help              | Display help. Issuing: help [command] , prints more specific help about "command"     |
 | version           | Show w3af version information.                                                        |
 | keys              | Display key shortcuts.                                                                |
 | http-settings     | Configure the HTTP settings of the framework.                                         |                                                                           |
 | misc-settings     | Configure w3af misc settings.                                                         |                                                                                          |
 | target            | Configure the target URL.                                                             |                                                                                               |
 | back              | Go to the previous menu.                                                              |
 | exit              | Exit w3af.                                                                            |
 | kb                | Browse the vulnerabilities stored in the Knowledge Base                               |
 -----------------------------------------------------------------------------------------------------------
 
* The http-settings and the misc-settings configuration menus are used to set system wide parameters that are used by  
  the framework. It is flexible enough to be used by both beginners and experts.
* All configuration menus provide the following commands for easy and quick configuration of scans

 |       Command     | Meaning                                        |
 |-------------------|------------------------------------------------|
 | view              | list the available options and their values    |
 | set               | set a parameter value                          |
 | save              | save the configured settings                   |
 | back              | go to previous menu                            |
 | exit              | exit w3af                                      |
  --------------------------------------------------------------------
  
* The scan can be started soon after configuring the desired plugins and followed by setting the targate URL.
* Once the plugin and framework configuration is set, it is possible to save this information to a profile, by using 
  'profiles' option.
