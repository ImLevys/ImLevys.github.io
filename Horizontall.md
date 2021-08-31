<h1>Hack the Box Horizontall walkthrough</h1>

<b>Find Subdomain in Javascript</b>
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/1-subdomain.png?raw=true)

<b>Search some intresting directories </b>
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/2-ffuf-subdomain.png?raw=true)

<b>Locate Strapi Version</b>
 ![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/3-strapi-version.png?raw=true)
 
 <b>Strapi CVE</b>
 
 The CVE is based on Authorezathion Bypass vulnerabillty, 
 you can reset admin's password without permissions.
 ![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/4-cve.png?raw=true)
 Link to the CVE: https://www.exploit-db.com/exploits/50239
 
<b>Exploit the CVE</b>
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/5-cve-exploit.png?raw=true)

<b>It worked!</b>
![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/6-login-admin.png?raw=true)

<b>Another Strapi CVE to get an RCE</b>

link to cve: https://github.com/dasithsv/CVE-2019-19609

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/7-cve-rce.png?raw=true)

Open a Listener on port 9001

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/7.5%20-%20listener%20on%20port%209001.png?raw=true)

Run the CVE Script

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/8-command-rce.png?raw=true)

<b>We got a shell</b>

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/9-rce.png?raw=true)

<b>First Flag</b>

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/10-userflag.png?raw=true)

<b>Download socat to victim machine</b>

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/13-socat_download.png?raw=true)

link to download socat: https://github.com/andrew-d/static-binaries/blob/master/binaries/linux/x86_64/socat

<b>Port forwarding PORT localhost:8000 to PORT 0.0.0.0:3333</b>

![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/14-socat.png?raw=true)
 
 <b>Laravel v8 PHP Framework</b>
 
 ![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/14-laravelphp.png?raw=true)
  
  <b>CVE of Laravel v8</b>
  
  link to the CVE: https://github.com/ambionics/laravel-exploits
  
  ![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/14.5%20laravel.png?raw=true)
  
  
  <b>Exploit the CVE</b>
  
  First of all we need to git clone the phpggc package from github
  
  Link to phpggc: https://github.com/ambionics/phpggc
  
  then run the command: 
  
  and it will generate a Exploit.phar file with the command "cat /root/root.txt"
  
  ![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/15-larvel_poc.png?raw=true)
  
  Then we can run the script to get root flag:
  
  ![alt text](https://github.com/ImLevys/ImLevys.github.io/blob/main/hackthebox/16-rooted.png?raw=true)
  
