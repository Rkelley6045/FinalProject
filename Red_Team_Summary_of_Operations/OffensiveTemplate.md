# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services
_TODO: Fill out the information below._

Nmap scan results for each machine reveal the below services and OS details:

![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Nmap%20/Nmap_Scan.png "Nmap Scan")

This scan identifies the services below as potential points of entry:
- Target 1
  - List of Exposed Servies: 
  - 22/TCP SSH
  - 80/TCP HTTP
  - 111/TCP rpcbind
  - 139/TCP netbios-ssn
  - 445/TCP netbios-ssn

_TODO: Fill out the list below. Include severity, and CVE numbers, if possible._

The following vulnerabilities were identified on each target:
- Target 1
  - List of critical vlunerabilites: 
  - Wordpress Pingback Locator 
  - Usernmae/Password Login Scanner 
  - XMLRPC DoS 
  - GHOST Vulnerability Scanner
  

_TODO: Include vulnerability scan results to prove the identified vulnerabilities._

### Exploitation
_TODO: Fill out the details below. Include screenshots where possible._

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_1.png "Flag 1")    
    - **Exploit Used**
      - _TODO: Identify the exploit used_
      - _TODO: Include the command run_
  - `flag2.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_2.png "Flag 2")   
    - **Exploit Used**
      - _TODO: Identify the exploit used_
      - _TODO: Include the command run_
  - `flag3.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_3.png "Flag 3")    
    - **Exploit Used**
      - _TODO: Identify the exploit used_
      - _TODO: Include the command run_
  - `flag4.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_4.png "Flag 4")    
    - **Exploit Used**
      - _TODO: Identify the exploit used_
      - _TODO: Include the command run_
