0. Simple web stack
mandatory
A lot of websites are powered by simple web infrastructure, a lot of time it is composed of a single server with a LAMP stack.

On a whiteboard, design a one server web infrastructure that hosts the website that is reachable via www.foobar.com. Start your explanation by having a user wanting to access your website.
1. Distributed web infrastructure
mandatory
On a whiteboard, design a three server web infrastructure that hosts the website www.foobar.com.
2. Secured and monitored web infrastructure
mandatory
On a whiteboard, design a three server web infrastructure that hosts the website www.foobar.com, it must be secured, serve encrypted traffic, and be monitored.
3. Scale up
#advanced
Readme

Application server vs web server
Requirements:

You must add:
1 server
1 load-balancer (HAproxy) configured as cluster with the other one
Split components (web server, application server, database) with their own server
You must be able to explain some specifics about this infrastructure:
For every additional element, why you are adding it
