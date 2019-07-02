# Description: Metasploit

### References
* [Metasploit Basic Terminologies](https://metasploit.help.rapid7.com/docs/metasploit-basics)
* [Getting Started with Metasploit](https://metasploit.help.rapid7.com/docs/getting-started)
* [Woring with Active and Passive Exploits]([](https://www.offensive-security.com/metasploit-unleashed/exploits/))
* [Working with Payloads](https://metasploit.help.rapid7.com/docs/working-with-payloads)
* [Metasploit Tutorial with Example](https://linuxhint.com/metasploit-tutorial/)
* [Metasploit : The Penetration Testing Guide](https://repo.zenk-security.com/Metasploit/Metasploit-The%20Penetration%20Tester%20s%20Guide.pdf)
* [Metasploit Basics](https://www.tutorialspoint.com/metasploit/metasploit_basic_commands.htm)

### Introduction
* Metasploit was originally developed and delivered by HD Moore. It is an entire framework that provides the 
  infrastructure to automate routine and complex tasks.
* It allows to concentrate on unique or specialized aspects of penetration testing and on identifying flaws within 
  Information Security programs. Metasploit allows to easily build attack vectors to execute its exploits, payloads, 
  encoders etc. in order to create and use more advanced penetration testing.
* It comes in both a command line interface and a graphical user interface.  
* To carry out Pentesting using Metasploit Framework, following steps are carried out
    - Identify the exploit that the target system is vulnerable to.
    - Search for the same exploits in metasploit. 
    - Choose then configure a pre-loaded exploit in the database.
    - Configure a related payload.
    - Encode the payload in order to hide it from IPS.
    - Execute the exploit.
* Note
    - Exploit is the code or script used to break into the system against an identified vulnerability.
    - Payload is a set of tasks initialed subsequent to an exploit, in order to maintain access to the compromised system </i>.
* Following are the list of commands available in Metasploit

|    Command            |   Description          |
|-----------------------|---------------------------|
|    ?                  |   Help menu           |
|    banner             |   Display an awesome metasploit banner    |
|    cd                 |   Change the current working directory    |
|    color              |   Toggle color    |
|    connect            |   Communicate with a host |
|    exit               |   Exit the console    |
|    get                |   Gets the value of a context-specific variable   |
|    getg               |   Gets the value of a global variable |
|    grep               |   Grep the output of another command  |
|    help               |   Help menu   |
|    history            |   Show command history    |
|    load               |   Load a framework plugin |
|    quit               |   Exit the console    |
|    repeat             |   Repeat a list of commands   |
|    route              |   Route traffic through a session |
|    save               |   Saves the active datastores |
|    sessions           |   Dump session listings and display information about sessions    |
|    set                |   Sets a context-specific variable to a value |
|    setg               |   Sets a global variable to a value   |
|    sleep              |   Do nothing for the specified number of seconds  |
|    spool              |   Write console output into a file as well the screen |
|    threads            |   View and manipulate background threads  |
|    unload             |   Unload a framework plugin   |
|    unset              |   Unsets one or more context-specific variables   |
|    unsetg             |   Unsets one or more global variables |
|    version            |   Show the framework and console library version numbers  |
----------------------------------------------------------------

* Module Commands

|    Command            |   Description         |
|-----------------------|----------------------------|
|    advanced           |   Displays advanced options for one or more modules   |
|    back               |   Move back from the current context  |
|    info               |   Displays information about one or more modules  |
|    loadpath           |   Searches for and loads modules from a path  |
|    options            |   Displays global options or for one or more modules  |
|    popm               |   Pops the latest module off the stack and makes it active    |
|    previous           |   Sets the previously loaded module as the current module |
|    pushm              |   Pushes the active or list of modules onto the module stack  |
|    reload_all         |   Reloads all modules from all defined module paths   |
|    search             |   Searches module names and descriptions  |
|    show               |   Displays modules of a given type, or all modules    |
|    use                |   Interact with a module by name or search term/index |
---------------------------------------------------

* Job Commands
|    Command            |   Description          |
|-----------------------|---------------------------|
|    handler            |   Start a payload handler as job  |
|    jobs               |   Displays and manages jobs   |
|    kill               |   Kill a job  |
|    rename_job         |   Rename a job    |
------------------------------------------

* Resource Script Commands

|    Command            |   Description           |
|-----------------------|----------------------------|
|    makerc             |   Save commands entered since start to a file |
|    resource           |   Run the commands stored in a file   |
-------------------------------------------------

* Database Backend Commands

|    Command            |   Description           |
|-----------------------|---------------------------|
|    analyze            |   Analyze database information about a specific address or address range  |
|    db_connect         |   Connect to an existing data service |
|    db_disconnect      |   Disconnect from the current data service    |
|    db_export          |   Export a file containing the contents of the database   |
|    db_import          |   Import a scan result file (filetype will be auto-detected)  |
|    db_nmap            |   Executes nmap and records the output automatically  |
|    db_rebuild_cache   |   Rebuilds the database-stored module cache   |
|    db_remove          |   Remove the saved data service entry |
|    db_save            |   Save the current data service connection as the default to reconnect on startup |
|    db_status          |   Show the current data service status    |
|    hosts              |   List all hosts in the database  |
|    loot               |   List all loot in the database   |
|    notes              |   List all notes in the database  |
|    services           |   List all services in the database   |
|    vulns              |   List all vulnerabilities in the database    |
|    workspace          |   Switch between database workspaces  |
--------------------------------------------------------

* Credentials Backend Commands
|    Command            |   Description              |
|-----------------------|-------------------------------|
|    creds              |   List all credentials in the database    |
-------------------------------------------------------

* Developer Commands

|    Command            |   Description               |
|-----------------------|--------------------------------|
|    edit               |   Edit the current module or a file with the preferred editor |
|    irb                |   Open an interactive Ruby shell in the current context   |
|    log                |   Display framework.log paged to the end if possible  |
|    pry                |   Open the Pry debugger on the current module or Framework    |
|    reload_lib         |   Reload Ruby library files from specified paths  |
----------------------------------------------------------

### Usage
* Steps to start Metasploit from terminal
```
service postgresql start 
msfdb init
msfconsole 
```

### Usage
```
# Terminate the first sessions
sessions -k 1

# Stop some extra running jobs
jobs -k 2-6,7,8,11..15

# Check a set of IP addresses
check 127.168.0.0/16, 127.0.0-2.1-4,15 127.0.0.255

# Target a set of IPv6 hosts
set RHOSTS fe80::3990:0000/110, ::1-::f0f0

# Target a block from a resolved domain name
set RHOSTS www.example.test/24
```
