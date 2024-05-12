# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

### Name: POOJA A
### Register No: 212222240072
### Date: 12-05-2024

## AIM
To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.

## PROGRAM
### Client :
```python 
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('connection closed')
```

### Server:
```python
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server listening on port", port)

while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'C:\\Users\\SEC\\Desktop\\Prabha.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```

## OUTPUT
![328116294-a48baf6c-284c-4b24-bcbc-0f062d9e8def](https://github.com/poojaanbu0/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/119390329/ec3b4c39-7d16-4b4e-bc11-bd1aa593adee)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
