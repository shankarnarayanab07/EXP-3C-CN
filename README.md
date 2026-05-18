# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
## Server.py
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server waiting for connection...")
while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    data = conn.recv(1024)
    print("Server received", repr(data))
    filename = 'mytext.txt'
    f = open(filename, 'rb')
    l = f.read(1024)
    while l:
        conn.send(l)
        print("Sent", repr(l))
        l = f.read(1024)
    f.close()
    print("Done sending")
    conn.send("Thank you for connecting".encode())
    conn.close()
```

## Client.py:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('mytext.txt', 'wb') as f:
    while True:
        print('Receiving data...')
        data = s.recv(1024)
        if not data:
            break
        print('Data =', data)
        f.write(data)
print('Successfully received the file')
s.close()
print('Connection closed')
```

## OUTPUT:
## Server:

<img width="1852" height="517" alt="server" src="https://github.com/user-attachments/assets/9f8539c8-279e-48d3-a1ea-bb7ceac2cf10" />


## Client:

<img width="1847" height="517" alt="client" src="https://github.com/user-attachments/assets/40395baf-5fe8-446a-ac55-aef6852ed5cc" />



## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
