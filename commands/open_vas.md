# Description: OpenVAS

### References 
* [Vulnerability Assessment with OpenVAS](https://www.hackingtutorials.org/scanning-tutorials/vulnerability-scanning-openvas-9-pt-1/)
* [Getting Started with OpenVAS](https://hackertarget.com/openvas-tutorial-tips/)
* [How to Run a Complete Scan with OpenVAS](https://www.techrepublic.com/article/how-to-run-a-complete-network-scan-with-openvas/)

### Introduction
* The Open Vulnerability Assessment Scanner (OpenVAS) is a network vulnerability scanner in Kali Linux. 
* It is developed and maintained by Greenbone Networks since 2009. 
* The works are contributed as Open Source to the community under GNU General Public License (GNU GPL). 
* OpenVAS helps in identifying vulnerabilities on the network side. It is one of the leading vulnerability scanners. 
* It is a suite of tools that work together to run tests against client systems using a database of known exploits and 
  weaknesses. 
* It includes around 47,000 vulnerabilities in its database.
* The GUI interface of OpenVAS is divided into following multiple menus

| OpenVAS GUI Menu      |   Purpose                                         |
|-----------------------|---------------------------------------------------|
| Dashboard             |   A customizable dashboard that presents information related to vulnerability management, scanned hosts, recently published vulnerability disclosures and other useful information. |
| Scans                 |   From here a new network vulnerability assessment scan can be started. All the reports and findings can be tracked under this menu. |
| Assets                |   All the accumulated hosts from the scans can be found. |
| SecInfo               |   The detailed information of all vulnerabilities and their CVE IDs are stored in SecInfo. |
| Configuration         |   Various options such as alerts, scheduling and reporting formats can be configured. Scanning options for host and open port discovery can also be customized using this menu. |
| Extras                |   Settings related to OpenVAS GUI, such as time and language can be done using this menu.    |
| Administration        |   Adding and deleting users and feed synchronization can be done through administration menu.   |

* It comes with the following capabilities
    - Unauthenticated testing
    - Authenticated testing
    - Various high level and low level Internet and Industrial protocols
    - Performance tuning for large-scale scans
    - Powerful internal programming language to implement any type of vulnerability test
* Vulnerability assessment using OpenVAS is achieved by
    - Creating and configuring a target
    - Creating and configuring a scan task
    - Running the scan
