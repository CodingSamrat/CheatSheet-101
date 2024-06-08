To install Nginx on Ubuntu 24.04 (or a similar recent version), you can follow these steps:

### 1. Update Package Index
``` bash 
sudo apt update
```

### 2. Install Nginx
Install Nginx using the apt package manager.
``` bash 
sudo apt install nginx
```

### 3. Start and Enable Nginx Service
Start the Nginx service and enable it to start on boot.
``` bash 
sudo systemctl start nginx
sudo systemctl enable nginx
```

### 4. Verify Nginx Installation
``` bash 
sudo systemctl status nginx
```

### 5. Adjust Firewall Settings
``` bash 
sudo ufw allow 'Nginx Full'
```

### 6. Verify Nginx is Serving Pages
Open a web browser and go to your server's IP address or domain name. You should see the default Nginx welcome page, which confirms that Nginx is installed and running correctly.

### 7. Configure Nginx
To configure Nginx, you will typically work with files in the /etc/nginx directory. The main configuration file is /etc/nginx/nginx.conf, and site-specific configurations are usually placed in the /etc/nginx/sites-available directory with symbolic links to /etc/nginx/sites-enabled.

**Example: Creating a Basic Website Configuration**

1. Create a configuration file for your site:
``` bash 
sudo nano /etc/nginx/sites-available/codingsamrat.com
```

2.  Add the following configuration:
``` bash 


```

3. 
``` bash 
# Configuration for Static site
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/example.com;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }
}



# Configuration for Express
server {
    listen 80;
    server_name codingsamrat.com www.codingsamrat.com;

    location / {
        proxy_pass http://localhost:5000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

4. Enable the site by creating a symbolic link:
``` bash 
sudo ln -s /etc/nginx/sites-available/codingsamrat.com /etc/nginx/sites-enabled/

```

5. Test the Nginx configuration for syntax errors:
``` bash 
sudo nginx -t
```


6. Reload Nginx to apply the changes:
``` bash 

```


8. Verify Your Site
Open a web browser and navigate to your domain (e.g., http://codingsamrat.com). You should see the HTML page you created.


## Summary of Commands
Here's a summary of the commands you need to install and configure Nginx:
``` bash 
sudo apt update
sudo apt install nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo ufw allow 'Nginx Full'
sudo nano /etc/nginx/sites-available/codingsamrat.com
sudo mkdir -p /var/www/codingsamrat.com
sudo nano /var/www/codingsamrat.com/index.html
sudo ln -s /etc/nginx/sites-available/codingsamrat.com /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx

```