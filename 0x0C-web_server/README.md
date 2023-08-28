0. Transfer a file to your server
mandatory
Write a Bash script that transfers a file from our client to a server:
1. Install nginx web server
mandatory
Readme:

-y on apt-get command
Web servers are the piece of software generating and serving HTML pages, let’s install one!
2. Setup a domain name
mandatory
.TECH Domains is one of the top domain providers. They are known for the stability and quality of their DNS hosting solution. We partnered with .TECH Domains so that you can learn about DNS.

.TECH Domains worked with domain name registrars to give you access to a free domain name for a year. Please get the promo code in your tools space. Feel free to drop a thank you tweet for .TECH Domains.

Provide the domain name in your answer file.
3. Redirection
mandatory
Readme:

Replace a line with multiple lines with sed
Configure your Nginx server so that /redirect_me is redirecting to another page.
4. Not found page 404
mandatory
Configure your Nginx server to have a custom 404 page that contains the string Ceci n'est pas une page.

Requirements:

The page must return an HTTP 404 error code
The page must contain the string Ceci n'est pas une page
Using what you did with 3-redirection, write 4-not_found_page_404 so that it configures a brand new Ubuntu machine to the requirements asked in this task
5. Install Nginx web server (w/ Puppet)
#advanced
Time to practice configuring your server with Puppet! Just as you did before, we’d like you to install and configure an Nginx server using Puppet instead of Bash. To save time and effort, you should also include resources in your manifest to perform a 301 redirect when querying /redirect_me.
