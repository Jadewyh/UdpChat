A simple UDP socket based chat application with a client and a server.

This project was something small I did for educational purposes as I'm interested in the nature and usecases of UDP.

Its simple and ugly, but it gives basic feedback and it works.

The server broadcasts messages it receives to all connected users.

TODO: <br/>
Let user set server IP from UI (serverIP can only be set in the code atm.) <br/>
List of users *DONE*<br/>
SocketError feedback *DONE*<br/>
Send Ack to client on connect *DONE*<br/>
Send Ack to client on disconnect<br/>
Send Ack to client on message<br/>

---Below is pure speculation, I did not read up on proper Ack techniques, these steps will involve quite a bit of overhead to confirm data is not corrupted and that it did arrive.---<br/>
Send Ack on msg (client saves all packets until they are acked from the server)<br/>
  -Add sequence number to Packet to keep track of them. <br/>
  -Server responds with full Packet it received, if any data was corrupted or did not arrive the client resends packet until proper Ack arrives. (timed interval might be good here, because of the low frequency nature of chatting)<br/>
  -Server doesnt broadcast until Client confirms data authenticity (server saves a list of unconfirmed packets until client ack data authenticity.<br/>
  -Server waits for all clients (not sender) to ack the message they recieved, before clearing the packet from its list of unconfirmed packets.<br/>
