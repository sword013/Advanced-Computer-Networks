# Bootstrap-Server

* Implemented a UDP Bootstrap server for registering services and facilitating client discovery by type, IP, and port.  
* Implemented a secure TCP file server that delivers requested files based on service type while validating access tokens.

## Part A

We have to Create a Bootstrap server that accepts the serving information from different servers like servicename, IP address, port number, and a service access token on UDP. Later it should allow a client asking for these servers' information on UDP.

### Steps

1. Open a terminal where the `udpserver.cpp` is stored.
   Compile and run `udpserver.cpp` by first:
   - Compiling: `g++ udpserver.cpp`
   - Running: `./a.out`
   
   This will create a bootstrap server that accepts the serving information from different servers like servicename, IP address, port number, and a service access token on UDP.

2. Now, open another terminal where the `Fileserver.cpp` is stored.
   Compile and run `Fileserver.cpp` by first:
   - Compiling: `g++ Fileserver.cpp`
   - Running: `./a.out`

   The program will ask for a Service type (input in the form of an integer), IP address, Port number, and Service Access token. It then sends this data to the bootstrap server where it is registered.
   - For example: `1 == PDF`, `2 == txt`, `3 == img`, etc.

   You can follow step 2 for other file servers like `imgserver`, `mp3_mp4server`, or `txtserver` by running the same `Fileserver.cpp` and providing different service types and info.

---

## Part B

Now we extend the file server program in Part A. Once it registers to the Bootstrap server successfully, it listens on a TCP socket. The server is intended to send a specific file to its clients depending on the service type.

1. Open a terminal where the `udpserver.cpp` is stored.
   Compile and run `udpserver.cpp` by first:
   - Compiling: `g++ udpserver.cpp`
   - Running: `./a.out`

2. Now, open another terminal where `Fileserver.cpp` is stored.
   Compile and run `Fileserver.cpp` by first:
   - Compiling: `g++ -pthread Fileserver.cpp`
   - Running: `./a.out`

   The program will ask for a service type, IP address, Port number, and Service Access token, which it sends to the bootstrap server. You can follow the same steps for other file servers by providing the appropriate information.

3. Now open the terminal where `Client.cpp` is stored.
   Compile and run `client.cpp` by first:
   - Compiling: `g++ client.cpp`
   - Running: `./a.out`
   
   The client fetches all the servers’ information from the Bootstrap server using UDP. It retrieves service name, respective IP address, port number, and an access token.

4. The program will ask the user to select a service type and enter its IP address, Port number, and Service Access token.
   
5. The respective file server checks if the Service Access Token (SAT) provided is valid. If invalid, it throws an error and informs the client.

6. If the SAT is valid, the program asks for the file path.

7. If the file path provided doesn't exist, the server informs the client and closes. If valid, the file is transferred and saved on the client system.

### Note:
The above program implements multithreading and can serve multiple clients in parallel.

---

## PLAGIARISM STATEMENT

I certify that this assignment/report is my own work, based on my personal study and/or research and that I have acknowledged all material and sources used in its preparation. I also certify that this assignment/report has not previously been submitted for assessment in any other course.

Name of the student: **Tejas Deshmukh**  
Roll No: **cs22mtech12005**
