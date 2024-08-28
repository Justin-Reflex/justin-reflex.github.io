
Ensure MySQL client is installed first: `sudo apt install default-mysql-client`

Everything here can also be done manually (ie. not using Metasploit):
https://nmap.org/nsedoc/scripts/mysql-enum.html
https://www.exploit-db.com/exploits/23081


Default info:
- Name: polomysql
- IP: 10.10.37.41
- credentials: "root:password"


![[Pasted image 20240614094613.png]]
- `mysql` is using port 3306/tcp


![[Pasted image 20240614095027.png]]
- tested known credentials: success


![[Pasted image 20240614095606.png]]
- performed a search for mysql modules, needed to find `mysql_sql`


![[Pasted image 20240614095956.png]]
- loaded module and listed options


![[Pasted image 20240614100400.png]]
- `set` necessary options then `run`
- discovery
	- version = `5.7.29-0ubuntu0.18.04.1`


![[Pasted image 20240614101227.png]]
- `set` sql to "show databases" instead of "select version()", then `run`
- discovery
	- there are 4 databases


![[Pasted image 20240614101930.png]]
- searched for "mysql_schemadump" to print out a list of tables and checked options


![[Pasted image 20240614102357.png]]
- after setting options (same as version discovery module), then `run`
- A bunch of table names print out, along with column information


![[Pasted image 20240614102819.png]]
- `use` new module for dumping hashes (possibly for passwords?), and go through `options`


![[Pasted image 20240614103028.png]]
- `set` options, same as for other modules


![[Pasted image 20240614103133.png]]
- successful hash dump
- discovery
	- another user: Carl


![[Pasted image 20240614105136.png]]
- `echo` the `username:hash` into a text file and check the file to validate
- could also open `nano` and paste hash, then exit and save as txt file


![[Pasted image 20240614105351.png]]
- `exit` Metasploit and run John the Ripper against the txt file
- discovery
	- password = doggie
- let's try the user and pass on ssh


![[Pasted image 20240614105621.png]]
- `ssh` onto the target IP using Carl username and password
- read MySQL.txt in default folder to find the flag
