---
layout: default
---

[Back Home](./index.md)

# TryHackMe - using enumeration to discover usernames/passwords in a MySQL database

Date: 6/14/2024

Default info:
- Name: polomysql
- IP: 10.10.37.41
- credentials: "root:password"

<br/><br/>
![Pasted image 20240614094613](https://github.com/user-attachments/assets/2a7d74d4-e22b-4cc8-ad4c-803796564f47)
- `mysql` is using port 3306/tcp

<br/><br/>
![Pasted image 20240614095027](https://github.com/user-attachments/assets/920dd1f8-44f3-45c7-a18f-0d90b0949118)
- tested known credentials: success

<br/><br/>
![Pasted image 20240614095606](https://github.com/user-attachments/assets/9a2b4c24-d39e-4463-848a-939c19ba8fe2)
- performed a search for mysql modules, needed to find `mysql_sql`

<br/><br/>
![Pasted image 20240614095956](https://github.com/user-attachments/assets/11f38860-7dc2-4284-9123-1462c183076d)
- loaded module and listed options

<br/><br/>
![Pasted image 20240614100400](https://github.com/user-attachments/assets/21c55754-34f7-4b21-a2a6-439531911732)
- `set` necessary options then `run`
- discovery
	- version = `5.7.29-0ubuntu0.18.04.1`

<br/><br/>
![Pasted image 20240614101227](https://github.com/user-attachments/assets/19d7e548-aba9-4692-9e3c-ebb7f6849aec)
- `set` sql to "show databases" instead of "select version()", then `run`
- discovery
	- there are 4 databases

<br/><br/>
![Pasted image 20240614101930](https://github.com/user-attachments/assets/f7ccf000-6c0c-474b-8611-d1bffc225fb6)
- searched for "mysql_schemadump" to print out a list of tables and checked options

<br/><br/>
![Pasted image 20240614102357](https://github.com/user-attachments/assets/1e527c1a-8e46-45a0-a8f7-457585772962)
- after setting options (same as version discovery module), then `run`
- A bunch of table names print out, along with column information


![Pasted image 20240614102819](https://github.com/user-attachments/assets/00a8a7bb-701c-4089-9986-b27a1aa2c803)
- `use` new module for dumping hashes (possibly for passwords?), and go through `options`

<br/><br/>
![Pasted image 20240614103028](https://github.com/user-attachments/assets/2791281d-523e-40cf-b13f-81a147ab39bf)
- `set` options, same as for other modules

<br/><br/>
![Pasted image 20240614103133](https://github.com/user-attachments/assets/2be80bb0-12ea-4aec-9556-1288b8fd9e9e)
- successful hash dump
- discovery
	- another user: Carl

<br/><br/>
![Pasted image 20240614105136](https://github.com/user-attachments/assets/44855409-766e-4590-a27b-78391d0dda2d)
- `echo` the `username:hash` into a text file and check the file to validate
- could also open `nano` and paste hash, then exit and save as txt file

<br/><br/>
![Pasted image 20240614105351](https://github.com/user-attachments/assets/caa3f93a-f85c-45ae-8818-06cc8837de52)
- `exit` Metasploit and run John the Ripper against the txt file
- discovery
	- password = doggie
- let's try the user and pass on ssh

<br/><br/>
![Pasted image 20240614105621](https://github.com/user-attachments/assets/5e445924-31b9-4d41-afd2-08f9fdcb9a66)
- `ssh` onto the target IP using Carl username and password
- read MySQL.txt in default folder to find the flag

<br/><br/>
[Back Home](./index.md)
