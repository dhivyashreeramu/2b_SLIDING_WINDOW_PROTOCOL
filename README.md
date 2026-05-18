# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a Python program for client-server communication using socket programming and implement sliding window protocol for frame transmission.

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
client side:
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
size=int(input("Enter number of frames to send : ")) 
l=list(range(size)) 
s=int(input("Enter Window Size : ")) 
st=0 
i=0 
while True: 
    while(i<len(l)): st+=s 
    c.send(str(l[i:st]).encode()) 
    ack=c.recv(1024).decode() 
    if ack: 
        print(ack) 
        i+=s
```
server side
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())

```

## OUPUT
client:
<img width="1782" height="828" alt="image" src="https://github.com/user-attachments/assets/96196577-2e1f-4e68-a356-027a4e662f64" />

server:
<img width="1789" height="835" alt="image" src="https://github.com/user-attachments/assets/6e489f0f-0088-4bfe-ace1-89da68923950" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
