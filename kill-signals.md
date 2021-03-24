The order in which kill signal must be used to stop a process are:  

Signal Name | Signal Value | Kill command
------------|--------------|-------------
SIGTERM     | 15           |kill 
SIGHUP      |  1           |kill -HUP or kill -1 
SIGKILL     |  9           |kill -9

kill -9 must not be used unless absolutely necessary. 
