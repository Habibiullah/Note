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
sudo firewall-cmd --permanent --add-service=http
```
Or
```
sudo firewall-cmd --permanent --add-p=80
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
 