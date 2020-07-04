# Recognisance & Intelligence Gathering
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

**Network Devices** 

- Protocal: SNMP
- Devices: Switch or Routers

| Level | Name| Example|
| ----- | ----| -------|
| 0 | Emergency| Failure causing shutdown |
| 1 | Alerts| Temperature exceeded |
| 2 | Critical| Software failure |
| 3 | Errors| Interface down |
| 4 | Warning| Config change |
| 5 | Notification| Protocol up/down |
| 6 | Informational| ACL violation |
| 7 | Debugging| Debug message |

- **Netflow** - Summery of traffic
- **Netstat** - Show active TCP/UDP connections
- **DHCP** - Logs in /var/log/dhcp.log
- **Firewall** - Contains ACLs & Logs
- **System Logs(Syslogs)** - /var/logs/
	- Application logs: Events logged by Apps/Programs
	- Security logs: Logins, file opened/deleted, recourse high usage
	- Setup logs : When apps start
	- System logs: events caused by windows components (OS logs)
	- Forwarded events: events from remote machines 
	
**DNS + Whois** 

- **IP Address Management**

  - **ARIN** - North America
  - **APNIC** - Asia Pacific
  - **RIPE** - Europe, Middle East
  - **LACNIC** - Latin America
  - **AfriNIC** - Africa

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

  - dig @server name type
  
  - dig axfr @dns-server domain.name
  
  - host -t axfr domain.name dns-server

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

- **Tools:** theHarvister, Maltego, Shodan
