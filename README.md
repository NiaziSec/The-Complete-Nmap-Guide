# The Complete Nmap Guide
A comprehensive resource covering everything about Nmap from basic commands to advanced scanning techniques. Perfect for beginners and professionals for network exploration and security auditing with Nmap.

## **Target Specification**
- **Single IP Scan**: `nmap <target>` - Scans a single IP (e.g., `nmap 192.168.1.1`).
- **Specific IPs Scan**: `nmap <target1> <target2>` - Scans specific IPs (e.g., `nmap 192.168.1.1 192.168.1.2`).
- **Range Scan**: `nmap <range>` - Scans a range of IPs (e.g., `nmap 192.168.1.1-254`).
- **Domain Scan**: `nmap <domain>` - Scans a domain (e.g., `nmap scanme.nmap.org`).
- **CIDR Scan**: `nmap <CIDR>` - Scans using CIDR notation (e.g., `nmap 192.168.1.0/24`).
- **Scan from File**: `nmap -iL <file>` - Scans targets from a file (e.g., `nmap -iL targets.txt`).
- **Random Hosts Scan**: `nmap -iR <count>` - Scans a specified number of random hosts (e.g., `nmap -iR 100`).
- **Exclude Hosts**: `nmap --exclude <target>` - Excludes specific hosts (e.g., `nmap --exclude 192.168.1.1`).

## **Scan Types**
- **TCP SYN Scan**: `nmap -sS <target>` - Default TCP SYN port scan (e.g., `nmap -sS 192.168.1.1`).
- **TCP Connect Scan**: `nmap -sT <target>` - TCP connect port scan (e.g., `nmap -sT 192.168.1.1`).
- **UDP Scan**: `nmap -sU <target>` - Scans UDP ports (e.g., `nmap -sU 192.168.1.1`).
- **Stealth Scans**: `nmap -sF | -sX | -sN <target>` - Perform stealth scans (e.g., `nmap -sF 192.168.1.1`).

## **Host Discovery**
- **Ping Scan**: `nmap -sn <target>` - Identifies live hosts (e.g., `nmap -sn 192.168.1.1`).
- **List Targets Only**: `nmap -sL <target>` - Lists targets without scanning (e.g., `nmap -sL 192.168.1.1-3`).
- **TCP ACK Scan**: `nmap -PA<ports> <target>` - Uses TCP ACK packets for discovery (e.g., `nmap -PA22,80 192.168.1.1`).

## **Port Scanning**
- **Single Port Scan**: `nmap -p <port> <target>` - Scans a specific port (e.g., `nmap -p 80 192.168.1.1`).
- **Port Range Scan**: `nmap -p <range> <target>` - Scans a range of ports (e.g., `nmap -p 21-100 192.168.1.1`).
- **All Ports Scan**: `nmap -p- <target>` - Scans all ports (e.g., `nmap -p- 192.168.1.1`).
- **Fast Scan**: `nmap -F <target>` - Scans the top 100 ports (e.g., `nmap -F 192.168.1.1`).

## **Service & Version Detection**
- **Service Version Detection**: `nmap -sV <target>` - Attempts to identify services and versions (e.g., `nmap -sV 192.168.1.1`).
- **Light Mode**: `nmap -sV --version-light <target>` - Faster detection with less accuracy (e.g., `nmap -sV --version-light 192.168.1.1`).
- **Aggressive Mode**: `nmap -sV --version-all <target>` - Enables all intensity levels (e.g., `nmap -sV --version-all 192.168.1.1`).

## **OS Detection**
- **OS Detection**: `nmap -O <target>` - Identifies the operating system (e.g., `nmap -O 192.168.1.1`).
- **Aggressive OS Guessing**: `nmap -O --osscan-guess <target>` - Performs aggressive guessing (e.g., `nmap -O --osscan-guess 192.168.1.1`).

## **Output**
- **Normal Output**: `nmap -oN <file> <target>` - Saves normal output to a file (e.g., `nmap -oN normal.txt 192.168.1.1`).
- **XML Output**: `nmap -oX <file> <target>` - Saves XML output to a file (e.g., `nmap -oX xml.txt 192.168.1.1`).
- **Open Ports Only**: `nmap --open <target>` - Shows only open ports (e.g., `nmap --open 192.168.1.1`).

## **Timing and Performance**
- **Speed Profiles**: `nmap -T<0-5> <target>` - Adjusts scan speed (e.g., `nmap -T4 192.168.1.1`).
- **Rate Limit**: `nmap --max-rate <rate> <target>` - Limits probes per second (e.g., `nmap --max-rate 100 192.168.1.1`).

## **Firewall Evasion Techniques**  
- **Timing and Throttling**: Adjust scan timing to avoid detection.  
  - Example: `nmap -T2 -Pn 192.168.1.1`  

- **Packet Fragmentation**: Split probes into fragments to evade firewalls.  
  - Example: `nmap -f 192.168.1.1`  

- **Custom MTU Size**: Set a custom MTU for packet fragmentation.  
  - Example: `nmap --mtu 16 192.168.1.1`  

- **Randomized Host Order**: Randomize the order of targets to evade detection.  
  - Example: `nmap --randomize-hosts -iL targets.txt`  

- **Decoys**: Use spoofed IPs to obfuscate the real scanner.  
  - Example: `nmap -D RND:10,ME 192.168.1.1`  

- **Spoofed Source IP**: Mask the scan source IP.  
  - Example: `nmap -S 1.2.3.4 192.168.1.1`  

- **MAC Address Spoofing**: Impersonate a MAC address.  
  - Example: `nmap --spoof-mac 00:11:22:33:44:55 192.168.1.1`  

- **Source Port Spoofing**: Mimic legitimate traffic using common service ports.  
  - Example: `nmap --source-port 53 192.168.1.1`  

- **Custom TTL**: Manipulate TTL to bypass firewall rules.  
  - Example: `nmap --ttl 128 192.168.1.1`  

- **Proxy Chains**: Route scans through proxies for anonymity.  
  - Example: `nmap --proxies proxylist.txt 192.168.1.1`  

- **Uncommon Protocols**: Use ICMP, SCTP, or other non-TCP/UDP protocols.  
  - Example: `nmap -PE 192.168.1.1`  

- **Random Payloads**: Add arbitrary data to confuse IDS.  
  - Example: `nmap --data-length 50 192.168.1.1`  

- **DNS Enumeration**: Perform DNS lookups instead of direct scans.  
  - Example: `nmap -sL 192.168.1.1/24`  

- **Combined Techniques**: Blend multiple evasion tactics for advanced scans.  
  - Example: `nmap -f -T2 -D RND:5 --spoof-mac 0 --source-port 443 192.168.1.1`  

## **Nmap Scripting Engine**  
- **dns-brute**:  
  - `nmap -p 80 --script=dns-brute [target]`  
  - `nmap --script=dns-brute --script-args dns-brute.domain=[domain] [target]`  

- **http-enum**:  
  - `nmap --script=http-enum [target]`  
  - `nmap --script=http-enum testhtml5.vulnweb.com`  
  - `nmap -sV --script=http-enum`  

- **ssh-brute**:  
  - `nmap -p 22 --script=ssh-brute [target]`  
  - `nmap -p 22 --script=ssh-brute --script-args userdb=users.txt,passdb=passwords.txt [target]`  

- **smb-enum-shares**:  
  - `nmap -p 445 --script=smb-enum-shares [target]`  
  - `nmap --script=smb-enum-shares --script-args smbuser=guest,smbpass=guest [target]`  

- **mysql-brute**:  
  - `nmap -p 3306 --script=mysql-brute [target]`  
  - `nmap --script=mysql-brute --script-args userdb=users.txt,passdb=passwords.txt [target]`

- **http-grep**:  
  - `nmap -p 80 --script=http-grep --script-args http-grep.url=<subpage>`  

- **http-config-backup**:  
  - `nmap -p 80 --script=http-config-backup`  

- **smb-enum-users**:  
  - `nmap --script=smb-enum-users [target]`  

- **http-wordpress-enum**:  
  - `nmap -p 80 --script=http-wordpress-enum [target]`  

- **firewalk**:  
  - `nmap --script=firewalk [target]`  

- **mysql-empty-password**:  
  - `nmap -p 3306 --script=mysql-empty-password [target]`  

- **mysql-users**:  
  - `nmap -p 3306 --script=mysql-users --script-args mysqluser=root,mysqlpass= [target]`
- 
- **mysql-brute**:  
  - `nmap -p 3306 --script=mysql-brute --script-args userdb=users.lst,passdb=pass.lst [target]`  

- **smb-os-discovery**:  
  - `nmap --script=smb-os-discovery.nse [target]`  
  - `nmap -p 445 --script=smb-os-discovery [target]`  

- **dns-zone-transfer**:  
  - `nmap --script=dns-zone-transfer.nse --script-args dns-zone-transfer.domain=[domain] [target]`  

- **ftp-anon**:  
  - `nmap --script=ftp-anon [target]`  

- **smtp-enum-users**:  
  - `nmap --script=smtp-enum-users --script-args smtp.domain=[domain] [target]`  

- **vulners**:  
  - `nmap --script=vulners --script-args mincvss=[value] [target]`  

- **snmp-brute**:  
  - `nmap --script=snmp-brute [target]`  

- **http-vuln-**:  
  - `nmap --script=http-vuln-* [target]`  

- **smb-enum-shares**:  
  - `nmap --script=smb-enum-shares [target]`  

- **http-title**:  
  - `nmap -p 80,443 --script=http-title [target-ip-or-domain]`  

- **ssl-cert**:  
  - `nmap -p 443 --script=ssl-cert [target-ip-or-domain]`  

- **vuln**:  
  - `nmap -p 80,443 --script=vuln [target-ip-or-domain]`  

- **http-robots.txt**:  
  - `nmap -p 80,443 --script=http-robots.txt [target-ip-or-domain]`  

- **ssh-hostkey**:  
  - `nmap -p 22 --script=ssh-hostkey [target-ip-or-domain]`  
 

## **Learn More**  
To deepen your understanding of Nmap, explore the following resources:  
- [Official Nmap Documentation](https://nmap.org/docs.html)  
- [Nmap Network Scanning Book](https://nmap.org/book/)  
- [SecTools Nmap Tutorials](https://sectools.org/tag/nmap/)
