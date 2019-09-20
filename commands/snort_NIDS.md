# Description : Snort Network Intrusion Detection System

### References 

* [Snort Ubuntu Tutorial](https://linuxhint.com/snort-ubuntu-tutorial/)
* [Configure Snort IDS Create Rules](https://linuxhint.com/configure-snort-ids-create-rules/)
* [How to Install Snort NIDS on Ubuntu](https://blog.rapid7.com/2017/01/11/how-to-install-snort-nids-on-ubuntu-linux/)
* [Secure Linux Server Using Snort NIDS](https://www.alibabacloud.com/blog/how-secure-your-linux-server-using-snort-nids_593775)
* [Using Snort For Intrusion Detection](https://www.techrepublic.com/article/using-snort-for-intrusion-detection/)

### Introduction

* Snort was initially developed in the year 1998, by DARPA.
* Snort is a free and opensource lightweight Network Intrusion Detection System.
* It is used to perform real-time traffic analysis and packet logging on IP networks.
* It allows creating rules in order to detect malicious traffic and alert the user.
* Snort has three operational modes, namely :
    * Sniffer
        - Sniffer mode only displays information about packet headers. 
        - `Example : ./snort -v  {will display TCP/IP packet headers}`
        
    * Packet Logger
        - It stores packets to the disk.
        - Stores packet payloads in different directories based on the type of protocol or IP class.
        - `Example : ./snort -dev -l ./log {will collect and place all packet payloads in the log directory}`
    
    * Network Intrusion Detection System
        - It can be used with stored packet and real-time traffic.
        - Network traffic is detected by implementing Snort rules on real-time traffic.
        - It is configured using `Snort configuration file - snort.conf`
        - It can be further configured as IPS to block network traffic by creating bridge network.
* A few of the operations that it can detect by monitoring the network traffic includes :
    
    - Buffer overflow detection
    - Stealth port scan detection
    - CGI attacks detection
    - Malicious activity detection
    - DoS attacks detection etc.
    
* `Usage : snort [-options] <filter options>` 

* Options list :

|   Option                                    |           Meaning                                                                                                                                 |
|---------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| -A                                          |   Set alert mode: fast/full/console/test or none                                                                                                  |
| -b                                          |   Log packets in tcpdump format                                                                                                                   |
| -B < mask >                                 |   Obfuscated IP addresses in alerts and packet dumps using CIDR mask                                                                              |
| -c < rules >                                |   Use Rules File <rules>                                                                                                                          |
| -d                                          |   Dump the Application Layer                                                                                                                      |
| -D                                          |   Run Snort in background (daemon) mode                                                                                                           |
| -e                                          |   Display the second layer header info                                                                                                            |
| -f                                          |   Turn off fflush() calls after binary log writes                                                                                                 |
| -F < bpf >                                  |   Read BPF filters from file < bpf >                                                                                                                |
| -g < gname >                                |   Run snort gid as <gname> group (or gid) after initialization                                                                                    |
| -G < 0xid >                                 |   Log Identifier (to uniquely id events for multiple snorts)                                                                                      |
| -h < hn >                                   |   Set home nework = < hn > (for use with -l or -B, does not change $HOME_NET in IDS mode)                                                           | 
| -H                                          |   Make hash tables deterministic                                                                                                                  |
| -i                                          |   Listen on interface < if >                                                                                                                        |
| -I                                          |   Add Interface name to alert output                                                                                                              |
| -k < mode >                                 |   Checksum mode (all/noip/notcp/noudp/noicmp/none)                                                                                                |
| -K < mode >                                 |   Logging mode (pcap/ascii/none)                                                                                                                  |
| -l < ld >                                   |   Log to directory < ld >                                                                                                                           |
| -L < file >                                 |   Log to this tcpdump file                                                                                                                        |
| -M                                          |   Log messages to syslog (not alerts)                                                                                                             |
| -m < umask >                                |   Set umask = < umask >                                                                                                                            |
| -n < cnt >                                  |   Exit after receiving < cnt > packets                                                                                                              |
| -N                                          |   Turn off logging (alerts still work)                                                                                                            |
| -O                                          |   Obfuscate the logged IP addresses                                                                                                               |          
| -p                                          |   Disable promiscuous mode sniffing                                                                                                               |
| -P < snap >                                 |   Set explicit snaplen of packet (default: 1514)                                                                                                  |    
| -q                                          |   Quiet. Don't show banner and status report                                                                                                      |
| -Q                                          |   Enable inline mode operation.                                                                                                                   |
| -r < tf >                                   |   Read and process tcpdump file < tf >                                                                                                              |
| -R < id >                                   |   Include 'id' in snort_intf< id >.pid file name                                                                                                    |
| -s                                          |   Log alert messages to syslog                                                                                                                    |
| -S < n=v >                                  |   Set rules file variable n equal to value v                                                                                                      |
| -t < dir >                                  |   Chroots process to < dir > after initialization                                                                                                   |
| -T                                          |   Test and report on the current Snort configuration                                                                                              |
| -u < uname >                                |   Run snort uid as < uname > user (or uid) after initialization                                                                                     |
| -U                                          |   Use UTC for timestamps                                                                                                                          |
| -v                                          |   Be verbose                                                                                                                                      |
| -V                                          |   Show version number                                                                                                                             |
| -X                                          |   Dump the raw packet data starting at the link layer                                                                                             |
| -x                                          |   Exit if Snort configuration problems occur                                                                                                      |
| -y                                          |   Include year in timestamp in the alert and log files                                                                                            |
| -Z < file >                                 |   Set the performonitor preprocessor file path and name                                                                                           |
| -?                                          |   Show this information `<Filter Options> are standard BPF options, as seen in TCPDump`                                                           |    
| --logid < 0xid >                            |   Same as -G                                                                                                                                      |
| --perfmon-file < file >                     |   Same as -Z                                                                                                                                      |
| --pid-path < dir >                          |   Specify the directory for the Snort PID file                                                                                                    |
| --snaplen < snap >                          |   Same as -P                                                                                                                                      |
| --help                                      |   Same as -?                                                                                                                                      |
| --version                                   |   Same as -V                                                                                                                                      |
| --alert-before-pass                         |   Process alert, drop, sdrop, or reject before pass, default is pass before alert, drop                                                           |
| --treat-drop-as-alert                       |   Converts drop, sdrop, and reject rules into alert rules during startup                                                                          |
| --treat-drop-as-ignore                      |   Use drop, sdrop, and reject rules to ignore session traffic when not inline.                                                                    |
| --process-all-events                        |   Process all queued events (drop, alert,...), default stops after 1st action group                                                               |
| --enable-inline-test                        |   Enable Inline-Test Mode Operation                                                                                                               |
| --dynamic-engine-lib < file >               |   Load a dynamic detection engine                                                                                                                 |
| --dynamic-engine-lib-dir < path >           |   Load all dynamic engines from directory                                                                                                         |    
| --dynamic-detection-lib < file >            |   Load a dynamic rules library                                                                                                                    |
| --dynamic-detection-lib-dir < path >        |   Load all dynamic rules libraries from directory                                                                                                 |
| --dump-dynamic-rules < path >               |   Creates stub rule files of all loaded rules libraries                                                                                           |
| --dynamic-preprocessor-lib < file >         |   Load a dynamic preprocessor library                                                                                                             |
| --dynamic-preprocessor-lib-dir < path >     |   Load all dynamic preprocessor libraries from directory                                                                                          |
| --dynamic-output-lib < file >               |   Load a dynamic output library                                                                                                                   |
| --dynamic-output-lib-dir < path >           |   Load all dynamic output libraries from directory                                                                                                |
| --create-pidfile                            |   Create PID file, even when not in Daemon mode                                                                                                   |
| --nolock-pidfile                            |   Do not try to lock Snort PID file                                                                                                               |
| --no-interface-pidfile                      |   Do not include the interface name in Snort PID file                                                                                             |
| --disable-attribute-reload-thread           |   Do not create a thread to reload the attribute table                                                                                            |
| --pcap-single < tf >                        |   Same as -r.                                                                                                                                     |
| --pcap-file < file >                        |   File that contains a list of pcaps to read - read mode is implied.                                                                              |
| --pcap-list "< list >"                      |   A space separated list of pcaps to read - read mode is implied.                                                                                 |
| --pcap-dir < dir >                          |   A directory to recurse to look for pcaps - read mode is implied.                                                                                |
| --pcap-filter < filter >                    |   Filter to apply when getting pcaps from file or directory.                                                                                      |
| --pcap-no-filter                            |   Reset to use no filter when getting pcaps from file or directory.                                                                               |    
| --pcap-loop < count >                       |   This option will read the pcaps specified on command line continuously. For < count > times.  A value of 0 will read until Snort is terminated. |
| --pcap-reset                                |   If reading multiple pcaps, reset snort to post-configuration state before reading next pcap.                                                    |    
| --pcap-reload                               |   If reading multiple pcaps, reload snort config between pcaps.                                                                                   |
| --pcap-show                                 |   Print a line saying what pcap is currently being read.                                                                                          |
| --exit-check < count >                      |   Signal termination after < count > callbacks from DAQ_Acquire(), showing the time it takes from signaling until DAQ_Stop() is called.             |    
| --conf-error-out                            |   Same as -x                                                                                                                                      |    
| --enable-mpls-multicast                     |   Allow multicast MPLS                                                                                                                            |    
| --enable-mpls-overlapping-ip                |   Handle overlapping IPs within MPLS clouds                                                                                                       |
| --max-mpls-labelchain-len                   |   Specify the max MPLS label chain                                                                                                                |    
| --mpls-payload-type                         |   Specify the protocol (ipv4, ipv6, ethernet) that is encapsulated by MPLS                                                                        |
| --require-rule-sid                          |   Require that all snort rules have SID specified.                                                                                                |
| --daq < type >                              |   Select packet acquisition module (default is pcap).                                                                                             |        
| --daq-mode < mode >                         |   Select the DAQ operating mode.                                                                                                                  |    
| --daq-var < name=value >                    |   Specify extra DAQ configuration variable.                                                                                                       |
| --daq-dir < dir >                           |   Tell snort where to find desired DAQ.                                                                                                           |
| --daq-list[=< dir >]                        |   List packet acquisition modules available in dir.  Default is static modules only.                                                              |
| --dirty-pig                                 |   Don't flush packets and release memory on shutdown.                                                                                             |    
| --cs-dir < dir >                            |   Directory to use for control socket.                                                                                                            |
| --ha-peer                                   |   Activate live high-availability state sharing with peer.                                                                                        |    
| --ha-out < file >                           |   Write high-availability events to this file.                                                                                                    |
| --ha-in < file >                            |   Read high-availability events from this file on startup (warm-start).                                                                           |
| --suppress-config-log                       |   Suppress configuration information output.                                                                                                      |
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------    

### Usage Examples    
````
* snort -A console -q -c /etc/snort/snort.conf -i eth0` <br>
    * Snort is up and listening on interface eth0. It will generate alerts to the console. 
* tcpdump -r /var/log/snort/snort.log <br>
    * Check the connection attempt on Snort server 
* snort -d -h 192.168.10.0 -l -c snort.conf <br>
    * Run snort for intrusion detection and log all packets relative to 192.168.10.0 network 
* snort -l /var/log/snort -b
    * To log packets in binary format to /var/log/snort     
* snort -dev -l /var/log/snort
    * To run snort in packet logging mode
* snort -v
    * To view IP packet headers at console            
````
