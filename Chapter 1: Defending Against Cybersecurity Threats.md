## Notes 
<details>
  <summary>Classmarker Test Notes</summary>
  <br>
  
  - PGP Key servers are public
  - DNS brute force can bypass IDP/IPS if slow enough as it can look like legit queries
  - nmap zone transfers would be detected by IPS
  - MBSA (Microsoft Baseline Security Analyzer) is free and would be used to check a windows server for security issues and give the most deail about it, as its ran with admin rights. (nessus and other vuln tools would give les details on patches installed)
  - MySQL = 3306
  - Oracle = 1521
  - Postgres = 5432
  - Microsoft SQL = 1433/1434
  - During investigation, if no login fails occured but last login was at weird time, most likley compromise
  -  Detection systems (honeypots) placed in otherwise unused network space will detect scans that blindly traverse IP ranges. Since no public services are listed, attackers who scan this range can be presumed to be hostile and are often immediately blocked by security devices that protect production systems.
  - Fast flux is a DNS technique used by botnets to hide phishing and malware delivery sites behind an ever-changing network of compromised hosts acting as proxies.
  - Decomposition diagram that maps the high-level functions to lower-level components. This will allow her to better understand how the malware package works and may help her identify areas she should focus on.
  - Trend = 
  - Heuristic = identify malware by examining the code in a virus program and analyzing the program's structure. A heuristic antivirus app using this detection method might run a process that simulates actually running the code it’s examining. When it does that, the antivirus app seeks to identify additional code logic that may help it determine if the suspected virus is really a threat.
  - Behavior = In comparason to what a thing usually would do. If you install an antivirus app that uses behavior detection, it watches your operating system, searching for suspicious events. For instance, if the antivirus program witnesses an attempt to change or modify a file or communicate over the Web, it may take action and warn you of the threat. It may also block the threat depending on how you adjust its security settings.
  - static analysis, which is analysis performed without running code. 
  - When endpoints are connected without a network control point between them, a host-based solution is required. In this case, Lucca’s specific requirement is to prevent attacks, rather than simply detect them, meaning that a HIPS is required to meet his needs. 
  - The best way to limit spam is to use a privacy or proxy service to register the domain. Many, if not most, popular registration services offer a privacy service, sometimes at an extra charge. Unfortunately, if a domain was previously registered before privacy services or proxies are used, that information can be looked up and used.
  -  A review of operational controls will often look at change management, separation of duties and other personnel controls, and process-based controls. Many administrative controls are part of an operational control review. These are sometimes conducted as Service Organization Control (SOC) audits with SOC 1, 2, and 3 reports generated depending on the level and depth of the assessment.
  - nmap’s Common Platform Enumeration is a standardized way to name applications, operating systems, and hardware. CPE output starts with cpe:/a for applications, /h for hardware, and /o for operating systems.
  - As attacks succeed, they will often create additional opportunities for discovery, resulting in more attacks. Planning the test itself, as well as the final reporting phase, should occur only once per penetration test.
  - Automated shunning, whether via an IPS or other technology, can block attackers but can also prevent penetration testers from being able to conduct scans or attacks. When planning a white-box penetration test, it is typical to discuss the presence of technologies that may block or limit the test and to either work around them or to disable them for the tester’s IP addresses if they are not directly in scope.
  - Back-off algorithm is a collision resolution mechanism which is used in random access MAC protocols (CSMA/CD). This algorithm is generally used in Ethernet to schedule re-transmissions after collisions.
  - auto shunning: Issuing the shun command blocks connections from an attacking host automatically(I.e IPS or other).
  - SIEM systems typically provide alerting, event and log correlation, compliance data gathering and reporting, data and log aggregation, and data retention capabilities. This also means that they can be used for forensic analysis as they should be designed to provide a secure copy of data. 
  - The three objectives of cybersecurity are confidentiality, integrity, and availability. Hashing and the use of integrity monitoring tools like Tripwire are both techniques used to preserve integrity; in fact, file integrity monitoring tools typically use hashing to verify that files remain intact and unchanged.
  
</details>
