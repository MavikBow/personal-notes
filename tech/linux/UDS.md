Unix Domain Socket  
  
is an inner-machine communication technology that uses 'socket'   
type files instead of a loopback network connection.  
  
Such files are stored entirely in RAM, making them faster  
than just using temp files.  
  
No need to worry about running out of TCP ports either.  
  
```plain text
    Client       Server    |    Client       Server   
                           |
   |------|     |------|   |   |------|     |------|  
   | HTTP |     | HTTP |   |   | HTTP |     | HTTP |  
   |------|     |------|   |   |------|     |------|  
   | TCP  |     | TCP  |   |   | UDS  | --> | UDS  |  
   |------|     |------|   |   |------|     |------|  
   | IP   |     | IP   |   |  
   |------|     |------|   |  
   | Eth  | --> | Eth  |   |  
   |------|     |------|   |  
  
```  
```nginx configuration file  
http {  
    server {  
        listen 443;  
        location / {  
            proxy_pass https://nodeserver;  
        }  
    }  
    upstream nodeserver {  
        server unix:/tmp/server.sock;  
    }  
}  
```  
  
It can do Server, Client, Reverse Proxy and Test.  
**It CANNOT do BROWSER.**  
  
[https://youtu.be/-WP_BIiVBo4]  
