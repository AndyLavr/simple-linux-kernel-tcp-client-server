# simple-linux-kernel-tcp-client-server
A simple in-kernel tcp client and server implemented as LKMs

This is an attempt to build a tcp server, entirely in kernel space, that supports mulitple tcp clients. The tcp client is also entirely in kernel space.

The client and server are built as loadable kernel modules.

## To try this out:
----------------

(1) clone this repo to server machine.\\
(2) open network_server.c\\ 
    change the port number of your server.
    sorry, this will soon be changed to module parameter.
(3) make
(3) sudo insmod network_server.ko
(4) keep observing dmesg out.
(5) clone this repo to client machine.
(6) before inserting the client, open network_client.c
    change the ip and port number to that of your server.
    again, this too will soon be changed to module parameters.
(7) make 
(8) sudo insmo  network_client.ko

## Status:
-------
Work still in progress.

## Note:
-----
Take care not to remove the server before the client(s) have been removed.
The server will be removed fine enough, but afterwards when you try to 
remove the client, you will run into trouble. This is because the client is
still waiting to hear, a response to its good bye, from a non-existant server. 
This will be rectified soon.

