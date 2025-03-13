# 2a_Stop_and_Wait_Protocol
# NAME:T.KAVINAJAI
# REGISTER NO: 212223100020

## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:

### SERVER:

```
import socket

server = socket.create_server(('localhost', 8000))
print("Server listening...")

conn, addr = server.accept()
print(f"Connected with {addr}")

while (data := conn.recv(1024).decode()):
    print(f"Received: {data}")
    conn.sendall(b"ACK")
    if data.lower() == 'exit':
        break

conn.close()
print("Connection closed")
```

### CLIENT:
```
import socket

client = socket.create_connection(('localhost', 8000))

while (msg := input("Enter message ('exit' to quit): ")):
    client.sendall(msg.encode())
    if msg.lower() == 'exit':
        break
    try:
        if client.recv(1024).decode() == "ACK":
            print("Server acknowledged")
    except socket.timeout:
        print("No ACK, retransmitting...")

client.close()
print("Connection closed")
```
## OUTPUT

### SERVER:

![image](https://github.com/user-attachments/assets/1d2957a1-e9b9-424a-9314-d1e462ea25db)

### CLIENT:
![image](https://github.com/user-attachments/assets/aa574bd6-5559-42fa-886f-d42be5839d80)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
