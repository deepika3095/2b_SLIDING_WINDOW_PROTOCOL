# NAME: DEEPIKA.R
# REG NO.: 212223230038
# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM: TO implement sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
# CLIENT:
import socket

s=socket.socket()

s.bind(('localhost', 8000))

s.listen(5)

c,addr=s.accept()

size=int(input("Enter number of frames to send : "))

l=list(range(size))

s=int(input("Enter Window Size : "))

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

# SERVER:
import socket

s = socket.socket()

s.connect(('localhost', 8000))

while True:

    print(s.recv(1024).decode())
    
    s.send("Acknowledgement received from the client".encode())

## OUPUT:
![Screenshot 2024-03-04 135336](https://github.com/deepika3095/2b_SLIDING_WINDOW_PROTOCOL/assets/151625159/6089194c-9104-4efe-888f-9754e4237cef)

![Screenshot 2024-03-04 135342](https://github.com/deepika3095/2b_SLIDING_WINDOW_PROTOCOL/assets/151625159/5381b358-8745-49a0-b1dc-17adddf353bf)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
