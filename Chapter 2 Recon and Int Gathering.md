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

Recon that does not involve "touching" the target at all.
Information that is publicly available about the target. 

### OSINT can be out of date!

If already in a system and looking to do passive recon you would be relying on stored data such as logs and configs.
This may not give you everything to ID target.
Firewall logs can be gold in terms of learning what isnt allowed through the firewall.


note: Many network devices by default log to their console port.

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










