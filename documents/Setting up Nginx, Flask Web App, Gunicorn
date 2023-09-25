# Setting up Nginx, Flask Web App, Gunicorn and Systemd within Debian Bulleyes Distribution

## Debugging with a Python path:

This function checks the python environment in the current user.

```
python3 -c "import sys; print(sys.path)"
```

This is the source of local user 
```
cd /home/tod/.local/lib/python3.9/site-packages
```

This command starts the Gunicorn proxy server
```
gunicorn --bind 0.0.0.0:5000 wsgi:app
```
```
# Please refer to some Gunicorn configuration file
Description=Gunicorn
```
[+] Command to set up gunicorn run as a service
``` bash
sudo vim /etc/systemd/system/tod.service
sudo systemctl start tod
sudo systemctl daemon-reload
sudo systemctl start tod
sudo systemctl enable tod
sudo systemctl status tod

```

- Take a look at the Gunicorn conf file, Reference: https://docs.gunicorn.org/en/stable/install.html
- How to debug nginx.service: Failed to parse PID from file /run/nginx.pid: Invalid argument.
Reference: https://bobcares.com/blog/failed-to-parse-pid-from-file-run-nginx-pid-invalid-argument/
- How to serve Flask application and Gunicorn
https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-18-04

For this debugging strategy on Nginx, I am using systemctl to debug and journalctl
```
sudo vim /etc/nginx/sites-available/tod.conf

# Content of the file tod.conf:
server {
    listen 80;
    server_name todk.taktivation.com;

    location / {
        include proxy_params;
        proxy_pass http://unix:/home/run/tod.sock;
    }

    location /static/ {
        root /home/tod/tps_tod;
    }
}

sudo ln -s /etc/nginx/sites-available/tod.conf /etc/nginx/sites-enabled

# I encounter the issues of nginx.service: Failed to parse PID from file /run/nginx.pid: Invalid argument
# Fix the resource

sudo tail -f /var/log/nginx/error.log

# Check all the group and see the 
getent group
```

Python environment path: PATH=/home/tod/env/teton/bin
```
[Unit]
Description=gunicorn daemon to run the tps_tod app
After=network.target

[Service]
User=
Group=www-data
WorkingDirectory=/home/tod/tps_tod
PATH=/home/tod/env/teton/bin
ExecStart=/home/tod/.local/bin/gunicorn --workers 4 --bind unix:/home/tod/run/tod_gunicorn.sock -m 007 wsgi:app

[Install]
WantedBy=multi-user.target
```
    sudo vim /etc/systemd/system/todgunicorn.service 
```
sudo systemctl restart todgunicorn
sudo systemctl restart nginx
sudo systemctl daemon-reload
```
```
sudo docker build -t tod:ubuntu-22.04 .
sudo docker run -it -d --rm -p 8080:8080 --name tod tod:ubuntu-22.04
sudo docker exec -it tod bash
sudo docker stop tod
```

Enviroment path
```
home/tod/.local/bin
/home/tod/.local/bin:/usr/local/bin:/usr/bin:/bin:
```
