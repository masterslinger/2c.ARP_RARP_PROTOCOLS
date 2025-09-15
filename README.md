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
Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"255.255.255.0":"68:34:21:7f:00:85","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```
Server
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
 
```

## OUPUT - ARP
<img width="869" height="280" alt="image" src="https://github.com/user-attachments/assets/9e4d105f-89c7-4eb6-9cdf-d828a9b205ec" />


## PROGRAM - RARP
client
```
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"68:34:21:7f:00:85":"255.255.255.0","68:34:21:7f:00:85":"255.255.255.0"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())

```
Server
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
   ip=input("Enter MAC Address : ") 
   s.send(ip.encode()) 
   print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
<img width="866" height="235" alt="image" src="https://github.com/user-attachments/assets/fbf976c2-3ba8-4b18-b156-82510c5dac6c" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
