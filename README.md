# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## Server--
```
import socket

host = '127.0.0.1'
port = 6000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((host, port))
server_socket.listen(1)

print("Server waiting for connection...")
conn, addr = server_socket.accept()
print("Connected to:", addr)

filename = "sample.txt"

with open("doc.txt", "rb") as file:
    data = file.read()
    conn.send(data).encode()

print("File sent successfully")
conn.close()
server_socket.close()   
```
## Client--
```
import socket

host = '127.0.0.1'
port = 6000

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))

with open("received_file.txt", "wb") as file:
    while True:
        data = client_socket.recv(1024)
        if not data:
            break
        file.write(data)

print("File received successfully")
client_socket.close()
```
## OUPUT
## Server--
<img width="1303" height="92" alt="serverout" src="https://github.com/user-attachments/assets/0830f8d4-09cb-4385-9b00-da0c304cb1d0" />

## Client--
<img width="1306" height="72" alt="clientout" src="https://github.com/user-attachments/assets/0dc74bad-367b-4ecb-84ab-f2c640ebaadf" />

## Received file--
<img width="455" height="117" alt="recfile" src="https://github.com/user-attachments/assets/d8beed9a-c2eb-4427-b4aa-572bcdde413e" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
