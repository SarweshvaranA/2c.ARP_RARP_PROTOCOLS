# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP:
### clieent.py
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```

### server.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP:
### clieent.py
![image](https://github.com/SarweshvaranA/2c.ARP_RARP_PROTOCOLS/assets/146930981/b40cf292-2255-4781-933c-66d42f350bf7)

### server.py
![image](https://github.com/SarweshvaranA/2c.ARP_RARP_PROTOCOLS/assets/146930981/43044b2d-783f-49ec-9537-b59c06befcb4)

## PROGRAM - RARP:
### clieent.py
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
    c.send(address[ip].encode())
 except KeyError:
    c.send("Not Found".encode())
```
### server.py
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP:
### clieent.py
![image](https://github.com/SarweshvaranA/2c.ARP_RARP_PROTOCOLS/assets/146930981/72329466-7690-48c7-ac63-5d0b04a4c555)

### server.py
![image](https://github.com/SarweshvaranA/2c.ARP_RARP_PROTOCOLS/assets/146930981/51b1e3c9-b46f-492b-b004-72ff9e5bc066)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
