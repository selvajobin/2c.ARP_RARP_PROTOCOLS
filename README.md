# EX 2c.SIMULATING ARP /RARP PROTOCOLS
### Register No: 212223220102
### Name: SELVA JOBIN S
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



## Client Program:
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
## Server Program:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical address: ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
![328745066-9473d293-579b-45c6-8ca4-ac7e6efd213f](https://github.com/selvajobin/2c.ARP_RARP_PROTOCOLS/assets/149985750/49f05783-0ee5-44be-9b0f-6533121cda23)


## PROGRAM - RARP
## Client Progam:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not found".encode())    
```
## Server Program:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter mac address: ")
    s.send(ip.encode())
    print("Logical address",s.recv(1024).decode())
```
## OUPUT -RARP
![328745353-a6286599-9fff-4c52-87f5-10f84989f680](https://github.com/selvajobin/2c.ARP_RARP_PROTOCOLS/assets/149985750/97c6301c-4da7-401c-98db-ef071574d8fd)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
