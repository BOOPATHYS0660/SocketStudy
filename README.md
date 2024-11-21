# Ex.No:2		  STUDY OF SOCKET PROGRAMMING AND CLIENT – SERVER MODE
## AIM: 
To implement socket programming date and time display from client to 
server using TCP Sockets 
## ALGORITHM : 
## Server: 
1. Create a server socket and bind it to port. 
2. Listen for new connection and when a connection arrives, accept it. 
3. Send server‟s date and time to the client. 
4. Read client‟s IP address sent by the client. 
5. Display the client details. 
6. Repeat steps 2-5 until the server is terminated. 
7. Close all streams. 
8. Close the server socket. 
9. Stop. 
## Client: 
1. Create a client socket and connect it to the server‟s port number. 
2. Retrieve its own IP address using built-in function. 
3. Send its address to the server. 
4. Display the date & time sent by the server. 
5. Close the input and output streams. 
6. Close the client socket. 
7. Stop.
## PROGRAM
## Client : 
```
import socket
from datetime import datetime
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
print("Client Address : ",addr)
now = datetime.now()
c.send(now.strftime("Date: %d/%m/%Y and Time: %H:%M:%S").encode())
ack=c.recv(1024).decode()
if ack:
    print(ack)
    c.close()
```
## Server :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
print(s.getsockname())
print(s.recv(1024).decode())
s.send("acknowledgement recived from the server".encode())
```
## OUTPUT:
CLIENT:
![Screenshot 2024-11-21 180817](https://github.com/user-attachments/assets/9a13344d-a883-4b9c-ae1f-6f5661f4d72d)

SERVER:
![Screenshot 2024-11-21 180835](https://github.com/user-attachments/assets/b55178a3-7e1f-4a92-b214-d3616787300e)

## RESULT:
Thus, the program to implement socket programming date and time display from client to 
server using TCP Sockets was successfully executed. 
