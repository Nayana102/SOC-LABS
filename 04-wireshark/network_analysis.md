Network Traffic Analysis & Protocol Triage

## Objective
To demonstrate proficiency in network forensics by capturing and analyzing fundamental protocols (DNS/ICMP) using Wireshark in a Windows environment.

## Lab Scenario: Baseline Connectivity Triage
In this practical lab, I analyzed the relationship between DNS resolution and ICMP connectivity to verify network health and identify host characteristics.

### 1. DNS Transaction Analysis (Layer 7)
* *Finding:* Identified a Standard Query for google.com.
* *Technical Detail:* Verified the *Transaction ID: 0xe515*.
* *Analyst Insight:* By matching the Transaction ID between the Query (Source: 10.21.77.xx) and the Response (Source: 10.21.77.xxx), I confirmed the integrity of the DNS exchange. This is a primary check to detect DNS spoofing or man-in-the-middle attacks.

### 2. ICMP Analysis & Path Triage (Layer 3)
* *Finding:* Successfully captured an ICMP Echo exchange.
* *TTL Analysis:* * *Outgoing TTL (128):* Fingerprinted the source as a Windows-based host.
    * *Incoming TTL (113):* Calculated a 15-hop distance to the target server ($128 - 113 = 15$).
* *Significance:* This demonstrates the ability to interpret Layer 3 headers to understand network topology and remote OS types.

### 3. Forensic Challenge: VPN Encapsulation
* *Challenge:* Initial capture showed only encrypted UDP/SSL traffic due to an active *Proton VPN*.
* *Resolution:* To achieve protocol visibility, I disabled the VPN and flushed the local DNS cache (ipconfig /flushdns). This highlighted the importance of "visibility" in security monitoring—encryption can often hide indicators of compromise (IOCs) from analysts.

## Tools Used
* Wireshark (Windows)
* Npcap
* Windows CMD (nslookup, ping, ipconfig)
