# Description: Nessus Vulnerability Scanner

### References
* [Nessus Official Website](https://docs.tenable.com/nessus/Content/GettingStarted.htm)
* [Introduction to Nessus Vulnerability Scanner](https://resources.infosecinstitute.com/a-brief-introduction-to-the-nessus-vulnerability-scanner/#gref)

### Introduction
* Nessus is an open source vulnerability scanner. 
* It consists of two parts - Engine and Plugins. 
    - Engine: The Engine reads each security checks from a file depending on the scan configuration and runs the check. 
    - Pluging: Plugins are security checks written in language supported by Nessus engine ie Nessus Attack Scripting 
      Language.
* Nessus Attack Scripting Language is used to find application vulnerabilities. It can be used to write custom Nessus 
  attack or a check that can find "killerapp.asp".
* Nessus
    - Tenable.io - Is a subscription based service. It allows different teams to share scanners, schedules, scan 
      policies and scan results.
    - Nessus Agents - Provide a flexible way of scanning hosts within environment without necessarily having to provide 
      credentials to hosts. The agents enable scans to be carried out even when the hosts are offline.
    - Nessus Professional - Is the most commonly deployed vulnerability assessment solution across the industry. It 
      helps to perform high-speed asset discovery, target profiling, configuration auditing, malware detection, 
      sensitive data discovery etc.

### Nessus Vulnerability Scan Methodology Followed 
* Execute Advanced Network Scan or Basic Network Scan on target IP address in Nessus Vulnerability Scanner.
* Based on Nessus findings, search and study CVE listed by it.
* Keep a track of risky vulnerabilities and report the same. Search for new Nessus Attack Scripting Language (NASL) 
  scripts to dig deep and ascertain the test result.
