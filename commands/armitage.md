# Description : Armitage 

### References
* [Armitage Setup](https://www.offensive-security.com/metasploit-unleashed/armitage-setup/)
* [Armitage Usage Tutorial](https://www.tutorialspoint.com/metasploit/metasploit_armitage_gui.htm)    
* [Armitage Exploitation](https://www.offensive-security.com/metasploit-unleashed/armitage-exploitation/)   

### Introduction
* Armitage is a complement tool for Metasploit created by Raphael Mudge. 
* It is the GUI version of Metasploit Framework. 
* It visualizes targets, recommends exploits and exposes the advanced post-exploitation features. 
* Armitage interface is feature rich and easy to use.
* Some of the best features available in Armitage are
    - Graphical User Interface (GUI)
    - Automatically recommends exploits
    - Exploit Browsing/ Custom Exploit
    - Exposes Metasploit's SOCKS proxy
* Armitage requires the following
    - Metasploit Framework and its dependencies (PostgreSQL Database and Nmap)
    - Oracle's Java 1.7
* Following are the steps carried out in Armitage to discover hosts and spot potential exploitable vulnerabilities in it
    * To launch Armitage run the command 'armitage'. During startup, select Start MSF, which will allow Armitage to 
      connect to the Metasploit instance.
    * After Armitage is running there are two ways to add hosts :
        * Manually adding the IP's that is on the target list.
        * Else find all hosts through Nmap Quick Scan by selecting `Hosts => Nmap Scan => Quick Scan(OS detect)`.
        * On selecting Nmap Quick Scan, fill out the range as per the series to be scanned, 
          `for example 192.168.179.0/24`
        * Armitage will scan the range or single IP address then present it in the black box.
    * Armitage GUI has three distinct areas: Targets, Console and Modules.
        * Targets list all the machines that have been discovered.
        * Console provides a view for the folders.
        * Modules is the section that lists the module og vulnerabilities.
    * Next is to find attacks by clicking Attacks => Find Attacks, which will automatically find all possible exploits for all targets.
    * Once the attack analysis has finished, an alert indicates that a menu is now available in right-click on the target by clicking Attack link.
    * After confirming an attack, click on "Use a reverse connection" and simply click on launch button.
    * The compromised host will appear in red. Thus post exploitation actions such as browsing files, taking screenshot of desktop, interacting with shell etc can be achieved.
