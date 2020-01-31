## Peer to Peer chat-post-search protocol

### Stablish a connection

First you need to open ports on your system to allow incoming/outgoing TCP connections.
You need python3 installed on your system. Otherwise you must modify code syntax to python 2.
Notice that you need to change default python version on your linux system using python peer-node.py command or use
python3 peer-node.py.
Server peer or generally each peer has a process(thread) running on port 50007, this process assigns a new port to 
any client peer requesting for connection.
Client peer as descirbed will connect to the port recieved from the port-server thread on server peer and the server
is automatically added to clients trust list, he can search for post in trusted peers later
Client either send arbitrary messages to server or requests to search for posts on all trusted peers, each peer 
recursively searches for the post in his trust list except he doesn't search in the ones that client peer already has.
client peer sends an array of IPs saying that he either has already searched the peers or he will do in the next iterations.
A clear drawback of the protocol is that it will iterate deep to the system and the first search connection may timeout.
This will be considered for the next commits that search only iterates 3-4 levels deep in the network trust graph.
The next problem is that client receives server messages along with the interface messages for the system, this is also
a serious problem to resolve.
