# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## Name:Yogaraj S
## Reg no: 212223040248
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter the number of frames to send:"))
l=list(range(size))
s=int(input("Enter window size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
## Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT:
![Screenshot 2024-10-19 134922](https://github.com/user-attachments/assets/743e46b7-505a-4c70-8abd-d2819db53065)
![Screenshot 2024-10-19 135004](https://github.com/user-attachments/assets/4eebf21b-52f3-43f3-94c2-d47a78600ee5)


## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed
