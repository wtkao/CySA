# Recognisance & Intelligence Gathering - 2

### <u>Footprinting</u>

Gathering information before the attack

**Active Reconnaissance** Port Scanning

| Well Known| Registered| Dynamic|
|---------- |---------- |--------|
| 0-1,023|1,024-49,151 |49,152 - 65,535|

### <u>Nmap Switches</u>

| Switch          | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| -sA             | ACK scan                                                     |
| -sF             | FIN scan                                                     |
| -sI             | IDLE scan                                                    |
| -sL             | DNS scan (list scan)                                         |
| -sN             | NULL scan                                                    |
| -sO             | Protocol scan (tests which IP protocols respond)             |
| -sP             | Ping scan                                                    |
| -sR             | RPC scan                                                     |
| -sS             | SYN scan                                                     |
| -sT             | TCP connect scan                                             |
| -sW             | Window scan                                                  |
| -sX             | XMAS scan                                                    |
| -A              | OS detection, version detection, script scanning and traceroute |
| -PI             | ICMP ping                                                    |
| -Po             | No ping                                                      |
| -PS             | SYN ping                                                     |
| -PT             | TCP ping                                                     |
| -oN             | Normal output                                                |
| -oX             | XML output                                                   |
| -T0 through -T2 | Serial scans.  T0 is slowest                                 |
| -T3 through -T5 | Parallel scans.  T3 is slowest                               |

- Nmap runs by default at a T3 level
- **Tools:** Nmap, Zenmap, Hping3, AngeryIP

**Passive Footprinting** Reading logs, passive log analysis

- <code>journalctl</code> View logs
- Cisco Router logs can be shown with the <code>show logging</code> command.

**Network Devices** 

- Protocal: SNMP - port 161
- SMNP Trap = Alert messege
- Devices: Switch or Routers
- **Management Information Base** (MIB) - database that stores information
- **Object Identifiers** (OID) - identifiers for information stored in MIB
- **SNMP GET** - gets information about the system
- **SNMP SET** - sets information about the system
- **Types of objects**
  - **Scalar** - single object
  - **Tabular** - multiple related objects that can be grouped together
- SNMP uses community strings which function as passwords
- There is a read-only and a read-write version
- Default read-only string is **public** and default read-write is **private**
- These are sent in cleartext unless using SNMP v3
- <code>enable</code> Heightens privilege on Cisco device. Similar to <code>Sudo</code>
- **Tools**
  - Engineer's Toolset
  - SNMPScanner
  - OpUtils 5
  - SNScan

| Level | Name		| Example			|
| ----- | --------------| ------------------------------|
| 0 | Emergency		| Failure causing shutdown 	|
| 1 | Alerts		| Temperature exceeded 		|
| 2 | Critical		| Software failure		|
| 3 | Errors		| Interface down 		|
| 4 | Warning		| Config change 		|
| 5 | Notification	| Protocol up/down 		|
| 6 | Informational	| ACL violation 		|
| 7 | Debugging		| Debug message 		|

- **Netflow** - Summery of traffic
  - Juniper’s Jflow and cflowd
  - Citrix’s AppFlow
  - HP’s NetStream
  - sFlow - sampled flow

- **DHCP** - Logs in /var/log/dhcp.log
- **Firewall** - Contains ACLs & Logs
- **System Logs(Syslogs)** - /var/logs/
	- Application logs: Events logged by Apps/Programs
	- Security logs: Logins, file opened/deleted, recourse high usage
	- Setup logs : When apps start
	- System logs: events caused by windows components (OS logs)
	- Forwarded events: events from remote machines 
- **Netstat** - Show active TCP/UDP connections
    - Shows open ports on computer
    - **netstat -a** displays both listening and non-listening
    - **netstat -an** displays connections in numerical form
    - **netstat -b** displays executables tied to the open port (admin only)
    - **netstat -o** displays information related to networking timers
    - **netstat -e** Display additional information. Use this option twice for maximum detail
    - **netstat -t** displays TCP
    - **netstat -u** displays UDP
    
- **Net**
    - **Net use** - lists network shares a device uses
    - **Net user** - shows local user accounts
    - **Net group** - domain controller command
    - **Net config** - allows services to be controlled
    
### <u>NetBIOS Enumeration</u>

- NetBIOS provides name servicing, connectionless communication and some Session layer stuff
- The browser service in Windows designed to host information about all machines within domain or TCP/IP network segment
- NetBIOS name is a **16-character ASCII string** used to identify devices
- Command on Windows is **nbtstat**
  - nbtstat (gives your own info)
  - nbtstat -n (gives local table)
  - nbtstat -A IPADDRESS (gives remote information)
  - nbtstat -c (gives cache information)

| Code | Type   | Meaning                   |
| ---- | ------ | ------------------------- |
| <1B> | UNIQUE | Domain master browser     |
| <1C> | UNIQUE | Domain controller         |
| <1D> | GROUP  | Master browser for subnet |
| <00> | UNIQUE | Hostname                  |
| <00> | GROUP  | Domain name               |
| <03> | UNIQUE | Service running on system |
| <20> | UNIQUE | Server service running    |

- NetBIOS name resolution doesn't work on IPv6
- **Other Tools**
  - SuperScan
  - Hyena
  - NetBIOS Enumerator
  - NSAuditor

### DNS + Whois

**DNS**

- **gTLD/** Generic Top Level Domian
	- .com
	- .org
	- .net
- **ccTLD/** Country Code Top Level Domain
	- .us
	- .ie
	- .co.uk
- **RIR/** Region Internet Registries
	- **ARIN** - North America
 	- **APNIC** - Asia Pacific
 	- **RIPE** - Europe, Middle East
 	- **LACNIC** - Latin America
 	- **AFRINIC** - Africa

- **Whois** - obtains registration information for the domain

- **Nslookup** - performs DNS queries

  - nslookup [ - options ] [ hostname ]
  - interactive zone transfer
    - nslookup
    - server <IP Address>
    - set type = any
    - ls -d domainname.com
	- MX = Mail
	- NS = Name servers
	- SOA = Start of authority
	- ALL = all

- **Dig** - unix-based command like nslookup

  - <code>dig @server name type</code>
  
  - <code>dig axfr @dns-server domain.name</code>
  
  - <code>host -t axfr domain.name dns-server</code>

- Zone transfer replicates all records

- **Name resolvers** answer requests

- **Authoritative Servers** hold all records for a namespace

- **DNS Record Types**

    | Name  | Description        | Purpose                                        |
    | ----- | ------------------ | ---------------------------------------------- |
    | SRV   | Service            | Points to a specific service                   |
    | SOA   | Start of Authority | Indicates the authoritative NS for a namespace |
    | PTR   | Pointer            | Maps an IP to a hostname                       |
    | NS    | Nameserver         | Lists the nameservers for a namespace          |
    | MX    | Mail Exchange      | Lists email servers                            |
    | CNAME | Canonical Name     | Maps a name to an A reccord                    |
    | A     | Address            | Maps an hostname to an IP address              |

- **SOA Record Fields**
  - **Source Host** - hostname of the primary DNS
  - **Contact Email** - email for the person responsible for the zone file
  - **Serial Number** - revision number that increments with each change
  - **Refresh Time** - time in which an update should occur
  - **Retry Time** - time that a NS should wait on a failure
  - **Expire Time** - time in which a zone transfer is allowed to complete
  - **TTL** - minimum TTL for records within the zone

- **DNS Tools:** theHarvister, Maltego, Shodan

- **Creepy:** geolocation tool for social media

- **EDGAR financial database:**  Public financial data

### Preventing Recognisance 

**Preventing Passive Recognisance**
-	Limit external exposure & services
-	Use a IPS
-	Use monitoring & alerting

**Preventing Active Recognisance**
-	Blacklist systems & networks
-	Use CAPTCHAS
-	User rate limiting
-	Don’t publish Zone Transfers 

____________________


<a href="https://github.com/ReefMeeter/CySA/blob/master/01.%20Defending%20Against%20CyberSecurity%20Threats.md"><< Previous</a> || <a href="https://github.com/ReefMeeter/CySA/blob/master/03.%20Designing%20a%20Vulnerability%20Management%20Program.md">Next >></a>  


<a href="https://github.com/ReefMeeter/CySA/blob/master/README.md">Return to Contents</a>
