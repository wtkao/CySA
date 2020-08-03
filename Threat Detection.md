**Pretexting** is a form of social engineering that relies on lies about the social engineer’s motives In this case, Fred is giving his targets reasons to believe he is legitimately a member of the organization’s support team  

**tag-out** sometimes refers to handing off to another member of a penetration test team, while profiling is conducted
 
**Automated shunning**, whether via an IPS or other technology, can block attackers but can also prevent penetration testers from being able to conduct scans or attacks  
 
**domain harvesting** -  relies on message rejection error messages to help the individual running the probe to determine which email accounts actually exist

nmap provides both hardware and operating system identification capabilities as part of its common platform enumeration features. cpe:/o indicates operating system identification, and cpe:/h indicates hardware identification.

## PORTS

### Databases

 - **Oracle** : 1512
 - **Postgress** : 5431
 - **MySQL** : 3306  
 - **MSSQL** : 1433,1434
 
 - **MSRCP** : 135 - for application to share processse remotly
 
 ### iptables
 3 chains
  - Inbount
  - Forwarded
  - Remote
  
  <code>iptables -L</code> Lists Rules  
  
  <code>iptables -A INPUT -s 10.10.10.10 -j DROP</code> Add a rule to end of list(Append)  
  
  <code>iptables -I INPUT -s 10.10.10.10 -j DROP</code> Add a rule to start of list(Insert)  
  
  <code>iptables -D INPUT <number></code> Delete rule <number>  
 
 
