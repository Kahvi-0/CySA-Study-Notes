# FOOTPRINTING

**Online guides:** 
- OSSTMM - http://www.isecom.org/research/
- Pentest Execution Standard http://www.pentest-standard.org/index.php/Main_Page
- SP 800-115 - https://csrc.nist.gov/publications/detail/sp/800-115/final

Mixture of info gathering techniques that will allow you to be able to make a map of an organization's networks, systems, 
and other infrastructure. These can be broken down into Active and Passice reconn.

<details>
<summary> Active Recon</summary>
 <br>
 Any recon that involves "touching" the targets systems.
 - host scanning
 - vulnerability scanning
 
Note: Scans can disrupt services on target systems, so make sure you have permission (can be illegal).
Big cloub providers such as MS Azure and Amazon Web Servics require a vulnerability or Pen Test Form 
before using their infrastructure for scans.

Traceroute, TTL, and responses from devices help map the targets Topology.

When using tools that generate a topology based on scans keep in mind that info may not be 100% accurate.

When scanning keep variables in mind such as wireless vs wired network and if there are VMs on scanned devices.

<details>
<summary>Port scanners:</summary>
 <br>
 Preform: 
 
  **Host Discovery -**
   Ping, just discovering the host.
  
  **Port Scanning/ Service ID -**
   PORTS: 
    Well Known or System Ports - 0 to 1023
    Registered - 1024 to 49151
 
   States:
    open - service is accessible
    closed - service is not accessible (pings may get a response that the port/ host is not found)
    filtered - firewall or similar is in place ( pings ususally not responsed to/ timeout)
 
  **Service Version ID -**
   Connecting to the port and grabbing its banner. Comparing its responses to signatures of known services.
 
   **OS ID -**
    Identifying the OS based on its network traffic/responses to scans.
    TCP/IP stack fingerprining that focus on comparing responses to TCP and UDP packets.
    TCP options they support, order the packets are sent in, and other details that can help guess the OS.


 <details>
 <summary>Common Tools</summary>
 <br>
 <details>
 <summary>Nmap/Zenmap:</summary>
 <br>
  -O OS discovery flag
  -sS SYN Scan
  -sT SYN Connect scan
  -sV Service Version Detection
  -p0 Skip pings
  - 
 </details>

  <details>
  <summary>Angry IP Scanner</summary>
  <br>
  Multiplatform Linux Win and MAC OS port scanner with a GUI
  Not as feature rich as NMAP
  Does not provide detailed ID of OS and services
  Requires Java
  </details>

  Other security tools have port scanning built in like Metasploit, Qualys Mgmt platform, and Nessus.

  </details>

  <details>
  <summary>Scan Techniques</summary>
  <br>
   - SYN Scan: Qucikest. Sends specially crafted SYN packets and wait for the SYN ACK. Then close the connection with a RST.
        Helps prevent logging as no connection occurred. MUST be root on a system to preform.
 
   - Connect Scan: A full TCP connection to the target. Preformed for possibly more accuracy and when root is not availble on scanning              host.
   - ACK Scans: Sending ACKs to help identify firewalls in conjunction with other scans.
  </details>
 </details>
</details>


<details>
 <summary>Passive Recon</summary>
 <br>

Good resource: https://www.securitysift.com/passive-reconnaissance/

Recon that does not involve "touching" the target at all.
Information that is publicly available about the target. 

### OSINT can be out of date!

If already in a system and looking to do passive recon you would be relying on stored data such as logs and configs.
This may not give you everything to ID target. 

If you are already on the target network you can do a packet capture.

DHCP logs or config file can give a lot of useful info such as static IP hosts which are ususally servers, logs of host(MACs) requests that will reveal hosts IPs currently in use, IP ranges.

Firewall logs can be useful by allowing you to reverse engineer the firewall rules to find out what is and isnt allowed through the firewall. You should also have access to the ACL.

System log files can provide info about how systems are configured, apps running on it, user accounts, and other details. Not top priority for recon. these are ususally sent off to a secure server.

**note** CySA+ includes Cisco, Palo Alto and Check Point firewalls. Formats for logs are similar.
**note** Cisco Firewall logs use identifiers https://www.cisco.com/c/en/us/about/security-center/identify-incidents-via-syslog.html
**note:** Many network devices by default log to their console port.

Organizational Intelligence can be a lot, but what is focused on is locations of buildings, how they are secured, business hours and workflow. Relationships between departments, employees, ORG charts, document analysis (metadata), financial data, Individuals.
This can be found on ORG sites, DB like EDGAR, social netoworks, and even social engineering.

Documents can provide ORG data whitin its metadata such as authors name, info on software used to create document, and sometimes revisions, edits, and other data. Cell phone photos can include GPS info. MIT Medial labs tool called Immersion provides info about who a user emails, this can help identify key contacts. A metadata scrubber can get rid of this information.

http://timetravel.mementoweb.org and http://archive.org will show older versions of a company website. Also googles cahce http://cacheview.com.

Social engineering tools like SET can help get a social engineering attempt setup. Creepy, a geolocation tool that uses social media and file metadata to help with social engineering. Metasploit includes phising and other tools. 


**Tools for Info Aggregation and Analysis:**
 theHarvester: gather emails, domain info, hostnames, employee names, and open ports and banners using search engines.
 Maltego: build relationship maps between people and their ties to other resources
 Shodan: search engine for internet connected devices and their vulnerabilities

<details>
 <summary>DNS</summary>
 <br>
 DNS is one of the first stops for recon. Publicily and easily obtained by a whois.
 nslookup DOMAIN Optional:specific DNS: on any OS for a domain will give you its DNS info. This can give access to info on the company     or its hosting service. Specific records can also be queried with -query flag=mx, ns, SOA, etc. DNS entries can contain hostnames that may give away the service its running.
 
 Domains names are mng by domain name registrars that are accredited by gTLD(generic TLD) and/or country ccTLD(Country code TLD). registrars provide the int between customer and domain registries, they handle purchase, billing, maintenance and transfers.
 
 Global IP space is managed by IANA. They manage the DNS Root Zone(that handles gTLD & ccTLD. Regional auth over these are handled by 5 RIRs (Regional Internet Registries):
  - AFRINIC = Africa
  - ARIN = USA, Canada, parts of Caribbean, and Antartica
  - APNIC = Asia, Aus, New Zealand, and other countries in the region.
  - LACNIC = Latin America and parts of Caribbean not covered by ARIN.
  - RIPE NCC = Central Asia, Europe, Middle East, and Russia.
 RIRs provide Whois info and other services to make sure IP and DNS for the Interent in the region are functioning. 
 
 If you find a DNS server running on a network, use dig or other DNS commands to test if it supports zone transfers. Most DNS server prohibit transfers to servers that arnt trusted DNS peers. 
 to test:
  - host -t axfr domain-name dns-server
  - dig axfr @dns-server domain-name
  
 **note** you can test this on digi.ninja. A site for practising zone transfers.
 **note** zone transfers is considered ACTIVE RECON
 **note** forward/reverse DNS lookups are considered ACTIVE RECON
 DNS brute forcing, if zone transfers are denied you can send DNS queries for each IP address that the ORG uses, that can provided answers. 
 
 Whois searches a DB of registered users of a domain, IP address block, and other interesting info such as location, admin contact info, phone numbers, emails, organization name, etc. This will vary from user to user.
 
 The host command in linux can also provide info on the systems IPv4 and IPv6 addresses and its email servers.
 
 **Historical domain data**
 domainhistory.net
 whoismind.com
Present historical data on info provided by whois.


</details>
 
 
<details>
 <summary>CISCO Log Level</summary>
 <br>
  - 0 Emergencies: Device shutdown due to failure
  - 1 Alerts: Temp limit exceeded
  - 2 Critical: Software fialure
  - 3 Errors: int down
  - 4 Warnings: Config change
  - 5 Notifications: Line protocol up/down
  - 6 Info: ACL violation
  - 7 Debug: debug mesg
</details>

Configs can give info such as syslog or SNMP remote servers. Details of those servers, configs , passwords, community strings, account info.



<details>
 <summary>Tools</summary>
 <br>
 Netflows: Cisco network protocol. Colletcs IP traffic. For monitoring. Flow data provides a view of traffic and volume. Along with netflows analyzer (like PRTC and SolarWinds) helps baseline and troubleshoot.
 
 Netstat: Unix and Windows tool. Active TCP/UDP connections filtered by TCP,UDP,ICMP,IP,IPv6 and others. 
   Linux:
   - ta list active TCP connections 
   - u  list active UDP connections 
   - w raw 
   - X unix socket connection 
   https://linux.die.net/man/8/netstat
    
   Windows:
   - e Ethernet statistics output for sent/recieved bytes, errors
   - o Displays active TCP connections and includes the PID for each connection 
   - nr routing table 
   https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/netstat
</details>





</details>










