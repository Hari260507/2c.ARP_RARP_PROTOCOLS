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
# server
```
import socket

s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
print("RARP Server listening on port 9000...")

c, addr = s.accept()
print("Connection from:", addr)

address = {
    "6A:08:AA:C2": "192.168.1.100",
    "8A:BC:E3:FA": "192.168.1.99"
}

while True:
    mac = c.recv(1024).decode()
    if not mac:
        break
    try:
        c.send(address[mac].encode())
    except KeyError:
        c.send("Not Found".encode())

c.close()
s.close()
```
# client
```
import socket

s = socket.socket()
s.connect(('localhost', 9000))

while True:
    ip = input("Enter logical Address : ")
    if ip.lower() in ['exit', 'quit']:
        break
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())

s.close()
```

## OUTPUT

<img width="1362" height="374" alt="image" src="https://github.com/user-attachments/assets/e74d82f8-c20a-4809-9b62-6822aff0e7d9" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
