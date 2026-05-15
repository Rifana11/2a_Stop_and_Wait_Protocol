# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
'''
SERVER CODE:
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()

CLIENT CODE:
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()

## OUTPUT
<img width="1877" height="947" alt="Screenshot 2026-05-15 091317" src="https://github.com/user-attachments/assets/4f2f5b8b-489a-40c1-8dd8-8f268b524e15" />
<img width="1177" height="887" alt="Screenshot 2026-05-15 091330" src="https://github.com/user-attachments/assets/f5cee50c-9d23-4307-a739-7761f9a1a143" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
