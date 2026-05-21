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
## PROGRAM - ARP

### Client:
### Developed By: VIDHYA SHREE K
### Register No: 212225230296
```
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
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
### Server
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/b5d8ce8a-0599-452e-94fe-af7f98d3e9fe" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/f78f03ca-8578-417d-81cb-f4993352c992" />


## PROGRAM - RARP
### Client 
```
import socket 
s=socket.socket() 
s.bind(('localhost',7000)) 
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
### Server
```
import socket 
s=socket.socket() 
s.connect(('localhost',7000))
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/64663ca1-bbf7-4be0-a66f-8c80668881c4" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/679c7fc1-c003-4761-ae1f-feb63c4d4ec2" />



## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
