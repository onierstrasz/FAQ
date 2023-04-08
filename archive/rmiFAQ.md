# RMI-FAQ

Q When I try to start my server, I get
  Binding //localhost:2001/GameServer ...
  Exception in thread "main" java.rmi.ConnectException: 
  Connection refused to host: localhost; nested 
  exception is: 
        java.net.ConnectException: Connection refused
  How do I fix this?
A Make sure you are using the real hostname to start
  the server.
A Make sure your firewalls are turned off on both the
  client and the server.
