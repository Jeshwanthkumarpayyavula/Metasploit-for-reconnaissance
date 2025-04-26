# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
# AIM:
To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .
## DESIGN STEPS:
### Step 1:
Install kali linux either in partition or virtual box or in live mode
### Step 2:
Investigate on the various categories of tools as follows:
### Step 3:
Open terminal and try execute some kali linux commands
## EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system
## OUTPUT:
![image](https://github.com/user-attachments/assets/443817c0-c117-46eb-8328-e8513761089d)

POSTGRESQL
msfdb :
![image](https://github.com/user-attachments/assets/c43be25b-0a92-4059-a66a-be7306ee8d62)

Invoke msfconsole:
## OUTPUT:
![image](https://github.com/user-attachments/assets/9ef463ad-ab9e-4819-ae51-6ae52a36ae5e)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
![image](https://github.com/user-attachments/assets/6247f566-50bb-4c41-ac7f-986197d19fd3)

## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![image](https://github.com/user-attachments/assets/42bf8e7c-c2dc-4c6a-9d13-0c5cae441057)

## Step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24
## OUTPUT:
![image](https://github.com/user-attachments/assets/7d8dadd5-df6e-4a5f-a34b-7514322a58ae)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l
## OUTPUT:
![8](https://github.com/user-attachments/assets/bed83ff5-0e61-4eca-ae78-7b64b93ed107)
Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit
## OUTPUT:
![image](https://github.com/user-attachments/assets/c7bb0461-a654-4c8a-9a10-0e162c191f61)

The info command provides information regarding a module or platform,
## OUTPUT:
![image](https://github.com/user-attachments/assets/06045c17-8fac-47c4-8c70-0afef2d8ddb3)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init
## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
## OUTPUT:
![11](https://github.com/user-attachments/assets/720c949b-8ea4-4ccc-be64-9bcb8405d431)
Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
## OUTPUT:
![image](https://github.com/user-attachments/assets/d669a1dd-09a2-4cf7-b005-a6746a93ef51)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
![13](https://github.com/user-attachments/assets/d0b191df-04a9-4861-b1a0-733ac33d7c5b)
Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
![image](https://github.com/user-attachments/assets/f2ca1201-ee24-467a-ae0a-035c95498a89)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
![image](https://github.com/user-attachments/assets/9b40f614-11b7-46ea-bec1-550ff13aa211)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
## OUTPUT:
![image](https://github.com/user-attachments/assets/5946f2f7-c883-4402-9564-1df32c3a6d75)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
