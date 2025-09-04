#### Python Socket Module Example

This repository demonstrates a simple client-server communication setup using Python's `socket` module. The code includes two scripts: `server.py` and `client.py`, which allow a server and client to exchange messages over a TCP connection.

##### Overview

The `socket` module in Python provides a way to create network applications by enabling communication between a server and one or more clients. This example sets up a basic chat application where:
- The **server** listens for incoming connections and exchanges messages with a connected client.
- The **client** connects to the server, sends messages, and receives responses.

Both scripts use TCP sockets for reliable, two-way communication over the loopback address (`127.0.0.1`) on port `5001`.

##### Files

- `server.py`: The server-side script that accepts a client connection, receives messages, and sends responses.
```python
import socket
host = "127.0.0.1"
port = 5001
server = socket.socket()
server.bind((host,port))
server.listen()
conn, addr = server.accept()
print ("Connection from: " + str(addr))
while True:
   data = conn.recv(1024).decode()
   if not data:
      break
   print (" from client: " + str(data))
   data = input("type message: ")
   conn.send(data.encode())
conn.close()
```
- `client.py`: The client-side script that connects to the server, sends messages, and receives responses.
```python
import socket
host = '127.0.0.1'
port = 5001
client = socket.socket()
client.connect((host,port))
message = input("type message: ")
while message != 'q':
   client.send(message.encode())
   data = client.recv(1024).decode()
   print ('Received from server: ' + data)
   message = input("type message: ")
client.close()
```
---
#### How It Works

##### Server (`server.py`)
1. Creates a TCP socket using `socket.socket()`.
2. Binds the socket to the host (`127.0.0.1`) and port (`5001`).
3. Listens for incoming connections with `server.listen()`.
4. Accepts a client connection, receiving a connection object and the client's address.
5. Enters a loop to:
   - Receive and decode messages (up to 1024 bytes) from the client.
   - Print the client's message.
   - Prompt the server user to type a response.
   - Send the response back to the client.
6. Closes the connection when the client sends an empty message (indicating disconnection).

##### Client (`client.py`)
1. Creates a TCP socket using `socket.socket()`.
2. Connects to the server at `127.0.0.1:5001` using `client.connect()`.
3. Enters a loop to:
   - Prompt the user to type a message.
   - Send the message to the server (encoded as bytes).
   - Receive and decode the server's response (up to 1024 bytes).
   - Print the server's response.
4. Exits the loop and closes the connection when the user types `q`.
---
#### Example Logs

###### Server Logs
```
Connection from: ('127.0.0.1', 59946)
 from client: Hi
type message: What do you want ?
 from client: I want to chat.
type message: ok the, press q ;)
```

###### Client Logs
```
type message: Hi
Received from server: What do you want ?
type message: I want to chat.
Received from server: ok the, press q
type message: q
```
---
##### Key `socket` Module Functions Used

- `socket.socket()`: Creates a new socket object.
- `socket.bind((host, port))`: Binds the socket to a specific address and port.
- `socket.listen()`: Enables the server to accept connections.
- `socket.accept()`: Accepts an incoming connection, returning a connection object and client address.
- `socket.connect((host, port))`: Connects the client to the server at the specified address.
- `socket.recv(buffer_size)`: Receives data (up to `buffer_size` bytes) from the socket.
- `socket.send(data)`: Sends data (as bytes) over the socket.
- `socket.close()`: Closes the socket connection.
---
##### Notes

- The server only handles one client connection at a time. To support multiple clients, you would need to use threading or asynchronous programming.
- The buffer size for `recv` is set to 1024 bytes, which is sufficient for short messages. For larger messages, you may need to handle data in chunks.
- The example uses `127.0.0.1` (localhost) for simplicity. To communicate over a network, replace the host with the server's IP address.
- Messages are encoded/decoded using UTF-8 (default for `encode()` and `decode()`).
---
##### Troubleshooting

- **Connection refused**: Ensure the server is running before starting the client and that the host/port match in both scripts.
- **Port already in use**: If the server fails to bind, try a different port number or ensure no other process is using port `5001`.
- **No response**: Ensure both client and server are running on the same network and the firewall allows traffic on the specified port.
---
