![[Pasted image 20251117214011.png]]
Nginx use for website Host, Custom Domain enable and Website secure. Nginx work for delivery. 
![[Pasted image 20251118151449.png]]
Terminal open in Server

For install Nginx
```
sudo apt-get install nginx -y
```
Nginx start
```
sudo systemctl start nginx
```
s
**Enable**
```
sudo systemctl enable nginx
```

status check
```
sudo systemctl status nginx
```


```
sudo ufw allow 'Nginx Full'
```

When it working then show active and running.
Check browser which write public -IP and screen display Welcome to nginx.
Enable HTTP service in firewalld
```
sudo firewall-cmd --permanent --add-service
```
Or
```
sudo firewall-cmd --permanent --add-p=80
```
 #  **when you setup in local**
# How to open port 80 and 443 on Ubuntu

### Step 1: Check if UFW is installed
sudo ufw status # for status if inactive then


```
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```
OR allow web services:

`sudo ufw allow 'Nginx Full'`

This automatically opens both 80 and 443.
Enable UFW (only if it is inactive)
```
sudo ufw enable
```
If you want to verify open ports
```
sudo ufw status
```
If you want to check which firewall you have

Nginx Configure # Nginx config location
```
cd /etc/nginx/
ls
```
For read app or read with vi or nano 
```
less nginx.conf
```


Server which
Config basic structure
![[Pasted image 20251118163014.png]]
Nginx http type request listen or work, server your website content where and who port listen.
![[Pasted image 20251118163735.png]]

Hosting Our Own Static Website
Enter in html
```
cd /user/share/nginx/html/
```
All files for delete in html
```
sudo rm -rf *
```
Directory create of Domain-name
```
sudo mkdir hb.com
```
Directory which enter
```
cd hb.come
```
Create html file and write which web-page
```
sudo vi index.html
```
html content
```
<html>
		<body>
				<h1>This is hb website</h1>
		</body>
</html?				
```
Nginx make and website configure
```
cd /etc/nginx/
```
Make copy backup file of Nginx.conf
```
sudo cp nginx.conf nginx.conf_bkp
```
Delete nginx.config and again make
```
sudo rm nginx.conf
sudo vi nginx.conf
```
Content write
/server which website related information, website who port listen.
```
events{}
http{
      server{ 
               listen 80;
               root /user/share/nginx/html/hb.com/;
      }
}
```

Configuration syntax check
```
sudo nginx -t
```
When syntax change then update 
```
sudo systemctl reload nginx.service
sudo systemctl status nginx.service
```
 Directory make
```
sudo mkdir about
cd about
```
 about which copy index.html, previous location html file copy in about 
 ```
sudo cp ../index.html . 
 ```
 
 Content about/index.html
 ```
<html>
		<body>
				<h1>This is about section</h1>
		</body>
</html?				 
 ``` 
 Changing Default HTTP Port
 ```
 events{}
http{
      server{ 
               listen 8080;
               root /user/share/nginx/html/hb.com/;
      }
}
 ```
 Again syntax change then update 
```
sudo systemctl reload nginx.service
sudo systemctl status nginx.service
```
Nginx Logging # cd /var/log/nginx/
ls
```
sudo less access.log
```
 For error log check
```
sudo less access.log
```
Hosting multiple websites 
cd /user/share/nginx/html/
sudo mkdir zn.com
cd zn.com
sudo nano index.html
content
# Static Website  

index.html  
```
<!DOCTYPE html>  

<html lang="en">  

<head>  

<meta charset="UTF-8">  

<meta name="viewport" content="width=device-width, initial-scale=1.0">  

<title>Professional Webpage Demo</title>  

<link rel="stylesheet" href="styles.css">  

</head>  

<body>  

<div class="container">  

<header class="header">  

<h1>Welcome to Our Professional Webpage</h1>  

<p>Delivering quality and excellence</p>  

</header>  

  

<main class="content">  

<section class="card">  

<h2>About Us</h2>  

<p>We are a team of dedicated professionals providing top-notch solutions tailored to your needs.</p>  

</section>  

  

<section class="card">  

<h2>Our Services</h2>  

<ul>  

<li>Custom Web Development</li>  

<li>Enterprise Software Solutions</li>  

<li>Cloud Integration Services</li>  

</ul>  

</section>  

  

<section class="card">  

<h2>Contact Us</h2>  

<p>Email: <a href="contact@professionalwebpage.com">contact@professionalwebpage.com</a></p>  

<p>Phone: +123-456-7890</p>  

</section>  

</main>  

  

<footer class="footer">  

<p>&copy; 2025 Professional Webpage. All Rights Reserved.</p>  

</footer>  

</div>  

</body>  

</html>
```

**styles.css**
sudo nano styles.css
content#
```
body {

font-family: 'Arial', sans-serif;

margin: 0;

padding: 0;

background: linear-gradient(to right, #1e3c72, #2a5298);

color: #333;

}

.container {

max-width: 800px;

margin: 0 auto;

padding: 20px;

text-align: center;

background-color: #ffffff;

border-radius: 12px;

box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);

}

.header {

padding: 20px;

border-bottom: 2px solid #ddd;

}

.header h1 {

font-size: 2.5rem;

color: #1e3c72;

}

.header p {

font-size: 1.2rem;

color: #555;

}

.content {

margin-top: 20px;

text-align: left;

}

.card {

background-color: #f9f9f9;

margin: 15px 0;

padding: 20px;

border-radius: 12px;

box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);

}

.card h2 {

font-size: 1.8rem;

color: #2a5298;

margin-bottom: 10px;

}

.card p, .card ul {

font-size: 1rem;

color: #444;

margin: 0;

}

.card ul {

list-style: none;

padding: 0;

}

.card ul li {

margin: 5px 0;

position: relative;

}

.card ul li::before {

content: '✔';

color: #2a5298;

margin-right: 8px;

font-weight: bold;

}

.card a {

color: #1e3c72;

text-decoration: none;

}

.card a:hover {

text-decoration: underline;

}

.footer {

margin-top: 20px;

padding: 10px;

background-color: #f9f9f9;

border-radius: 12px;

font-size: 0.9rem;

color: #555;

box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

}
```

**==error.html==**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Error</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            height: 100vh;
            
          } 
          h1 {
            font-size: 4rem;

            margin-bottom: 1rem;

          }

          p {

			font-size: 1.5rem;

			margin-bottom: 2rem;

			}

			a {

			  text-decoration: none;

			  background-color: #007bff;

			  color: #fff;

              padding: 0.75rem 1.5rem;

              border-radius: 5px;

              font-size: 1rem;

            }

            a:hover {

               background-color: #0056b3;

            }
           </style>
          </head>
          <body>
             <h1>Oops!Something went wrong.</h1>
             <p>We couldn't find the page you were looking for or encountered an              error.</p>
             <a href="/">Return to Homepage</a>
            </body>
            </html>
```
After make index.html and styles.css   # cd ..    and edit nginx.config 
 sudo nano /nginx/nginx.conf/
 Setup MIME Types
 sudo less mime.types
 ```
 events{
	worker_connections 1024; 
}
http{
		include mime.types;
	    server{ 
			    s
                listen 80;
                root /var/www/html/hb.com/;
                index index.html;
        }
        #zn.com
        server{ 
		        server_name zn.com;
                listen 80;
                root /var/www/html/zn.com/;
        }
}
 ```
check syntax and reload file
sudo nginx -t
sudo systemctl reload nginx.service

zn.com folder which add files      *index.html , styles.css*

 # Fixing styles.css
 
sudo systemctl reload nginx.service

**Nginx Configure Custom Domain**
Custom Domain configure
Register a domain name.
In DNS settings, create a A record and point to public IP of our server (EC2).
IN nginx.conf, server block, use
   &server_name www.hb.com
(Hostinger through buy domain), (Domain purchasing)
DNS setup

     Configure Eroor Page and Logs
Add website folder which error.html file and content write.
Create error.html or 404.html    #samething
configure nginx.conf
```
events{

worker_connections 1024;

}

http{

include mime.typs;

  

server{

s

listen 8080;

root /var/www/html/abg-store.com/index.html;

index index.html;

}

  

server{

server_name zn.com www.vsttechnologies.com;

listen 80;

root /var/www/html/zn.com/;

index index.html;

  

error_page 404 /error.html;

  

access_log /var/log/nginx/zn.com.access.log;

error_log /var/log/nginx/zn.com.error.log;

}

}
```
sudo nginx -t
sudo systemctl reload nginx.service
sudo systemctl status nginx.service

For logs check
```
cd /var/log/nginx
ls -ltr
```

Nginx Conf which some changing

```
events{

worker_connections 1024;

}

http{

include mime.typs;

  

server{

s

listen 8080;

root /var/www/html/abg-store.com/index.html;

index index.html;

}

  

server{

server_name zn.com www.vsttechnologies.com;

listen 80;

root /var/www/html/zn.com/;

index index.html;

  

error_page 404 /error.html;

location / {
		try_files $uri $uri/ =404;
}
  

access_log /var/log/nginx/zn.com.access.log;

error_log /var/log/nginx/zn.com.error.log;

}

}
```
Again reload nginx conf

                **Nginx Enable HTTPS**

HTTPS Setup
HTTPS is a secure version of HTTP that encrypts data between your browser and a website, making it safe from hackers.    
It usses SSL/TLS to protect sensitive information like passwords and credit card details.

**For MAC**
```
brew install certbot
```
**For Windows**
```
choco install certbot -y
```
**For Linux**
   Centos
   ```
   sudo apt install epel-release -y
   Or
   sudo apt install certbot pythone3-certbot-nginx -y
   ```
   Ubuntu
   ```
   sudo apt install certbot python3-certbot-nginx -y
   ```

**SSL /TLS**
   SSL is Secure Sockets Layer /Transport Layer Security
Cryptographic protocols designed to provide secure communication over  computer network.
TLS is the successor to SSL. TLS is latest version of SSL and use for security purpose.
**How SSL/TLS Secure data**
Encrypt data between client and server. (one point to another point which communication )
Encrypt data and ensure its
SSL/TLS three principles confidentiality, integrity and authenticity and principles archives use three methods encryption, hashing and certificates.


==Confidentiality==  Data is only accessed by client/server           ==Encryption==
                                            
==Integrity==             Data is not modified in between                     ==Hashing== 
		     			                 
==Authenticity==     Verifying the identity of the parties                ==Certificates==
		     who they are supposed to be
 
**Encyption**
          Converting plaintext information into a coded form (cipher text).
          (msg change other form, the other person access but not read msg).
          For example my message is DEMO -->GHPR  i am changing DEMO in GHPR (Cipher text, each character shifted by 3 char)
Encrypt   message is         DEMO -->GHPR
        shifting each char by 3 forward            
Decrypt  message is        GHPR --> DEMO
        shift each char by 3 backward
*Encrypt 2 types
   1) Symmetric                  2) Asymmetric
   
**Symmetric** 
Encrypt   message is         DEMO -->GHPR
   key=3    shifting each char by 3 forward            
Decrypt  message is        GHPR --> DEMO
   key=3   shift each char by 3 backward
**Asymmetric**
Encrypt   message is         DEMO -->GHPR
   key=3    shifting each char by 3 forward            
Decrypt  message is        GHPR --> DEMO
 key=23  shift each char by 23 backward
 Encrypt is public key
 Decrypt is private key
 
 Asymmetric encryption is used to securely exchange a symmetric key between parties.
 Symmetric encryption is faster and more efficient making it idealfor encryptinf large amount of data.
Some Algorithm Examples
Asymmetric                                                                Symmetric
  DSA                                                                             AES
  RSA                                                                             3DES
  ECC                                                                             RC4
  ECDH

**How real life AES encryption looks like...**

**Message:** DEMO

**Key 256 bit HEX:**  
cb5a6cefcf5b7e88f9bff6f27f32d6095a86db829d8518cf8edb6af2740ff8eb

**Initialization Vector (IV):**  
a8d246bb6ebae2b0e7651843b3053384

**AES-256-CBC Encryption:**  
8?Q3?B??Z)07??h??

**HASHING**
Hashing is the process of converting data into a fixed-size string of characters, as a sequence of numbers and letters.
**DEMO** → 37 (4 + 5 + 13 + 15 = 37)
**Alphabet:**  
ABCDEFGHIJKLMNOPQRSTUVWXYZ

**MESSAGE AUTH CODE (MAC)**  
**Combining MESSAGE + CODE**
**Message:** DEMO  
**Secret Key:** key123
**DEMOkey123 → 84**
**Alphabet:**  
ABCDEFGHIJKLMNOPQRSTUVWXYZ

**Most Common Hashing Algo**

- **MD5** (Message Digest Algorithm 5) (128 bits)
- **SHA** (Secure Hash Algorithm)
    - sha-1
    - sha-2/3 224 256 384 512
Hmac = **Hash-based Message Authentication Code (sha256hmac)**
 For example
 cho DEMO | sha     
sha1hmac    sha224hmac   sha256hmac   sha384hmac   sha512hmac
sha1sum     sha224sum    sha256sum    sha384sum    sha512sum     /any code select 

echo DEMO | sha512hmac
1f47aed161a7befa46204f4c351fa69e2a25d39de8a36d4afc66927728279508cfb7a7bbf9c230b222dbbd56e0a26893838d3b730f34ac2a1f7e26ad1a9ea6c

**Authentication**
**CA**     is certificate authority
**A Certificate Authority (CA)** is a trusted organization that issues digital certificates to verify the identity of websites and enable secure, encrypted communication over the internet.
**CAs** ensure the authenticity and integrity of the SSL certificates they provide.

**Formats for digital certificates**

|**Format**|**Encoding**|**Common Extensions**|**Usage**|**Contains Private Key**|
|---|---|---|---|---|
|PEM|Base64|.pem, .crt, .cer|Web servers, email|No (unless it’s a key file)|
|DER|Binary|.der, .cer|Java platforms, binary data handling|No|
|PKCS#7|Base64 or Binary|.p7b, .p7c|Certificate chains|No|
|PKCS#12|Binary|.p12, .pfx|Export/import certs with keys|Yes|
Setup in Server
Terminal open in Server

For install Nginx
```
sudo apt-get install nginx -y
```
Nginx start
```
sudo systemctl start nginx
```
status check
```
sudo systemctl status nginx
```

When it working then show active and running.
Check browser which write public -IP and screen display Welcome to nginx.
Enable HTTP service in firewalld
```
sudo firewall-cmd --permanent --add-service
```
Or
```
sudo firewall-cmd --permanent --add-p=80
```

HTTP setup in ubuntu
   ```
   sudo apt install certbot python3-certbot-nginx -y
   ```
   

- **First stop the nginx** (if listening on port 80) as below command will use local port 80.
```
sudo systemctl stop nginx.service
```
    
- **To generate certificates**
    
    `sudo certbot certonly --standalone -d yourdomain.com`
- **Files will be generated in**
    
    `/etc/letsencrypt/live/yourdomain.com/`


Enter Email address    
	Show public and private certificate key
```
listen 443 ssl http2;

ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;

ssl_protocols TLSv1.2 TLSv1.3;
```

***SSL**
```
server
{
listen 80;
listen 443 ssl;
ssl on;
ssl_certificate /etc/letsencrypt/live/yourdomain.com/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/yourdomain.com/privkey.pem;
access_log /var/log/nginx/zn.com.access.log;
error_log /var/log/nginx/zn.com.error.log;
}
```



sudo nano nginx.conf
 ```
events{

worker_connections 1024;

}
http {
    include mime.types;

    server {
	    server_name hbgarments.duckdns.org;
        listen 80;
        root /var/www/html/hbgarments.duckdns.org/index.html;
    }

    # ssl
    server {
        server_name hbgarments.duckdns.org www.hbgarments.duckdns.org;

        listen 443 ssl http2;

        root /var/www/html/hbgarments.duckdns.org/;

        index index.html;
		ssl_certificate /etc/letsencrypt/live/hbgarments.duckdns.org/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/hbgarments.duckdns.org/privkey.pem;

		ssl_protocols TLSv1.2 TLSv1.3;
        

    
	
        error_page 404 /404.html;

        location / {
            try_files $uri $uri =404;
        }

        access_log /var/log/nginx/hbgarments.duckdns.org.access.log;

        error_log /var/log/nginx/hbgarments.duckdns.org.error.log;

    }
}

 
 ```
sudo nginx -t
sudo systemctl start nginx.service
sudo systemctl status nginx.service
CDN77 website through 
 
**let's Encrypt  group provide free certificate and  Go Daddy and digicert**
                 
**Reverse Proxy**                 

**An Nginx reverse proxy** acts as an intermediary between clients and backend servers.

It forwards client requests to the appropriate server, handles responses, and provides benefits like load balancing, caching, and security.

**Userdata script to install and run ubuntu Webserver**
#!/bin/bash
sudo apt update -y
Install ubuntu web server (httpd) 
sudo apt install -y httpd 
sudo systemctl start httpd 
sudo systemctl enable httpd  
Create a simple HTML file to verify the web server is running 
```
echo "<<html><h1>This is Website 1</h1></html>" > /var/www/html/index.html

```

ngin.conf
```
events{}
https{
		include mime.type;
		server{
				listen 8080;
		        location /{
					proxy_pass http://instance-ip(backend public-ip)/;
				}
		}
}
```
sudo nginx -t
sudo systemctl reload nginx.service
nginx server public-ip backend sever security which http  in public-ip set

**Nginx Load Balancing**
  **Nginx load balancing** is a feature where Nginx distributes incoming traffic across multiple backend servers to ensure no single server gets overloaded, improving performance, reliability, and scalability of your application.
  Create instances for load balancing.
  
 ```
 events{

worker_connections 1024;

}
http {
	    include mime.types;
		upstream backend_servers {
        server 127.0.0.1:3000;
        server 127.0.0.1:3001;
        server 127.0.0.1:3002;
    server {
	        listen 8080;
	#       root /var/www/html/abg-store.com/index.html;
            location /{
					proxy_pass http://backend-servers/;
			}
    }

    # zn.com
    server {
        server_name zn.com www.vsttechnologies.com;

        listen 443 ssl http2;

        root /var/www/html/zn.com/;

        index index.html;
        

    ssl_certificate /etc/letsencrypt/live/myexamplewebsite.xyz/fullchain.pem;
	ssl_certificate_key/etc/letsencrypt/live/myexamplewebsite.xyz/privkey.pem;

	ssl_protocols TLSv1.2 TLSv1.3;
	
        error_page 404 /404.html;

        location / {
            try_files $uri $uri =404;
        }

        access_log /var/log/nginx/zn.com.access.log;

        error_log /var/log/nginx/zn.com.error.log;
} 
```

**Nginx Backup Server**
  Backup Server will only serve in case of Primary Fail
  ```
  upstream backend {
    server 192.168.1.1:3000;
    server 192.168.1.2:3000;
    server 192.168.1.3:3000 backup;
}
  ```

**Nginx Timeout**


# Frontend (Client-Side) Timeouts
client_header_timeout 10s;
client_body_timeout 10s;
send_timeout 15s;
keepalive_timeout 20s;

# Backend (Upstream Server) Timeouts
proxy_connect_timeout 5s;
proxy_read_timeout 30s;
proxy_send_timeout 30s;

 **Nginx Catching**
     **Nginx caching** is a process where Nginx stores copies of responses (like HTML, images, or API data) to serve them directly to users, reducing backend load and improving response times.
     
 Caching setup
 ```
 http {
    # Define the cache path
    proxy_cache_path /var/cache/nginx levels=1:2 keys_zone=my_cache:10m inactive=60m max_size=1g;

    server {
        listen 80;
        server_name example.com;

        location / {
            proxy_cache my_cache;  # Enable caching using the defined cache
            proxy_cache_valid 200 60m;  # Cache 200 OK responses for 60 minutes
            proxy_cache_key "$scheme$request_uri";  # Define the cache key
            proxy_pass http://backend_server;  # Forward requests to the backend server
            add_header X-Cache-Status $upstream_cache_status;  # Add cache status header for debugging
        }
    }
}
 ```

**hbgarments.duckdns.org**