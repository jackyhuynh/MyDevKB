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
