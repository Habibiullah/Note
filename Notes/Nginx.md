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
```
sudo systemctl status ufw
sudo systemctl status firewalld
```

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

styles.css
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

error.html
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
 ```
 events{}
http{
      server{ 
               listen 80;
               root /user/share/nginx/html/hb.com/;
      }
      #zn.com
      server{
                listen 80;
                root /user/share/nginx/html/zn.com/;
      }
}
 ```
check syntax and reload file
sudo nginx -t
sudo systemctl reload nginx.service
 
 # Fixing styles.css
 Setup MIME Types
 sudo less mime.types
setup css
sudo nano nginx.conf
```
 events{}
http{ 
        include mime.types;
        server{ 
                listen 80;
                root /user/share/nginx/html/hb.com/;
        }
        #zn.com
        server{
                listen 80;
                root /user/share/nginx/html/zn.com/;
                index index.html;
        }
}
```
sudo systemctl reload nginx.service

**Nginx Configure Custom Domain**
Custom Domain configure
Register a domain name.
In DNS settings, create a A record and point to public IP of our server (EC2).
IN nginx.conf, server block, use
   &server_name www.hb.com
(Hostinger through buy domain), (Domain purchasing)
   
