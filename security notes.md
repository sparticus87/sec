Stack  USERNAME    PASSWORD        JUMPBOX-IP
13 	ANSP-007-M 	QZozUJFIeaiguQQ 	10.50.33.89
=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
CTFD 10.50.20.103:8000
Lin-ops = 192.168.65.20 // 10.50.29.245
Win-ops = 192.168.65.10 // 10.50.32.34
=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
Penetration Testing
  What is Pen Testing??
    -Pen Testing 
**Phase 1: Mission Definition**
    -Define mission goals and targets
    -Determine scope of mission
    -Define RoE
**Phase 2: Recon**
  -Information gathering about the target through public sources
**Phase 3: Footprinting**
  -Accumulate data through scanning and/or interaction with the target/target resources
**Phase 4: Exploitation & Initial Access**
  -Gain an initial foothold on network
**Phase 5: Post-Exploitation**
    -Establish persistence
    -Escalate privileges
    -Cover your tracks
    -Exfiltrate target data
**Phase 6: Document Mission**
  -Document and report mission details
**Penetration Test Reporting**
  -Operation Notes (OPNOTES) vs Formalized Reporting
**Penetration Test Reporting**
    -Executive Summary
    -Technical Summary
**Penetration Test Reporting**
    -Reasons to report
    -What to report
    -Screen captures
=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
Vulnerability and Exploitation Research
**Initial Access**
    -What is initial access?
    -What is now the most common method for gaining initial access?                                  
                     Phishing!
**Initial Access**
What are some other techniques to gain initial access?
**Introduction to Exploit Research**
    Transition from reconnaissance to weaponization
    Leverage intelligence/data about network
    Pair vulnerabilities to exploits
    Align exploits to operational objectives
**Research**
    Open sources
    Organizational capabilities
**Capabilities**
    Mission Objectives drive requirements
        Collection
        Effects
    Additional functionality to fulfill requirements
    Communications security (COMSEC)
**Testing**
    Exploit Development occurs from vulnerability pairing and mission-drivens requirement
        Test and verify success
    Testing provides a number of benefits:
        Faster time to breakout of initial foothold
        Reduced risk of detection and/or tool failure
        Improved recovery times
**Plan**
    Procure Hardware and software
    Assign developer
    Assign a tester to develop TTPs and break it
    Document testing results
    Testing environment
=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
Network Reconnaisance and Scanning 
**Open Source Intelligence**
During the lesson we will review the following topics:
    Appropriate Documentation Practices
    Use of Collected Data
    Collection Methods
DoD States:
"produced from publicly available information that is collected, exploited, and disseminated in a timely manner to an appropriate audience for addressing a specific intelligence requirement."
**Documentation**
    Why is it important?
    What should we include in documentation?
**Collection and Use**
    What do we want to collect?
    How can it be used in operations?
**Limitations on Collection**
    Are there rules that guide our operations and collection parameters?
    What are important factors when collecting data about a target?
**Data to Collect**
    Web Data
    Sensitive Data
    Publicly Accessible
    Social Media
    Domain and IP Data
**Hyper-Text Markup Language (HTML)**
Standardized markup language for browser interpretation of webpages
    Client-side interpretation (web browser)
    Utilizes elements (identified by tags)
Typically redirects to another page for server-side interaction
Cascading Stylesheets (CSS) for page themeing
**HTML**
DEMO: Simple HTML page
**http://10.50.XX.XX/webexample/htmldemo.html**
Demonstration
Data collection through scraping
Scraping Data
**Prep**
pip install lxml requests
**Script**
#!/usr/bin/python
import lxml.html
import requests
page = requests.get('http://quotes.toscrape.com')
tree = lxml.html.fromstring(page.content)
authors = tree.xpath('//small[@class="author"]/text()')
print ('Authors: ',authors)
**What will it output?**
Authors:  ['Albert Einstein', 'J.K. Rowling', 'Albert Einstein', 'Jane Austen', 'Marilyn Monroe', 'Albert Einstein', u’Andr\xe9 Gide', 'Thomas A. Edison', 'Eleanor Roosevelt', 'Steve Martin']
**Advanced Scanning Techniques**
    Host Discovery
        Find hosts that are online
    Port Enumeration
        Find ports for each host that is online
    Port Interrogation
        Find what service is running on each open/available port     
**Demonstration**
Advanced Scanning Techniques
**NMAP Scripting Engine**
During the lesson we will review the following topics:
    Benefits of Scanning with Scripts
    Script Management and Utilization
    Usage and Examples
**Nmap Project States:**
"(It) allows users to write (and share) simple scripts to automate a wide variety of networking tasks. Those scripts are then executed in parallel with the speed and efficiency you expect from Nmap."
**Benefits**
    Why use scripts, instead of normal scanning options?
    Why are scripts important?
**Main Benefits**
    Network Discovery
    Sophisticated Version Detection
    Vulnerability Detection
    Backdoor Detection
    Vulnerability Exploitation
**Script Management**
Scripts are stored in a subdirectory of the Nmap data directory by default:
/usr/share/nmap/scripts
**Usage and Examples**
nmap --script <filename>|<category>|<directory>
nmap --script-help "ftp-* and discovery"
nmap --script-args <args>
nmap --script-args-file <filename>
nmap --script-help <filename>|<category>|<directory>
nmap --script-trace
**Demonstration**
Usage of Nmap NSE

for i in {1..254}; do (ping -c 1 172.16.82.$i | grep "bytes from" &) ; done

Scheme of Maneuver:
>jump box
-> network scan 192.168.28.96/27
--> network scan 192.168.150.224/27
nmap scripts
  --script=http-enum <ip>
  

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=


























































































































































































































































































































































































































































































































































































































