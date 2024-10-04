# Setting up Nginx, Flask Web App, Gunicorn, and Systemd on Debian Bullseye

## Debugging with Python Path

To check the Python environment for the current user:

```bash
python3 -c "import sys; print(sys.path)"
```

Navigate to the local user’s Python packages directory:

```bash
cd /home/tod/.local/lib/python3.9/site-packages
```

## Running the Gunicorn Proxy Server

Start the Gunicorn server with the following command:

```bash
gunicorn --bind 0.0.0.0:5000 wsgi:app
```

### Setting Up Gunicorn as a Service

Create a systemd service file for Gunicorn:

```bash
sudo vim /etc/systemd/system/tod.service
```

Once the service file is configured, you can manage the service with these commands:

```bash
sudo systemctl start tod
sudo systemctl daemon-reload
sudo systemctl enable tod
sudo systemctl status tod
```

### Gunicorn Configuration
Refer to the [Gunicorn documentation](https://docs.gunicorn.org/en/stable/install.html) for details on setting up a custom configuration file.

## Nginx Configuration for Flask and Gunicorn

Create a configuration file for your Nginx server:

```bash
sudo vim /etc/nginx/sites-available/tod.conf
```

Example content of the file:

```nginx
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
```

Link the configuration to `sites-enabled`:

```bash
sudo ln -s /etc/nginx/sites-available/tod.conf /etc/nginx/sites-enabled
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

Check for any issues by inspecting the error log:

```bash
sudo tail -f /var/log/nginx/error.log
```

If you encounter the error `Failed to parse PID from file /run/nginx.pid: Invalid argument`, refer to this [Nginx debugging guide](https://bobcares.com/blog/failed-to-parse-pid-from-file-run-nginx-pid-invalid-argument/) for troubleshooting.

## Gunicorn Systemd Configuration

To run Gunicorn as a service, configure the service file:

```bash
sudo vim /etc/systemd/system/todgunicorn.service
```

Service file content:

```ini
[Unit]
Description=gunicorn daemon to run the tps_tod app
After=network.target

[Service]
User=tod
Group=www-data
WorkingDirectory=/home/tod/tps_tod
ExecStart=/home/tod/.local/bin/gunicorn --workers 4 --bind unix:/home/tod/run/tod_gunicorn.sock -m 007 wsgi:app

[Install]
WantedBy=multi-user.target
```

Enable and start the service:

```bash
sudo systemctl restart todgunicorn
sudo systemctl daemon-reload
sudo systemctl enable todgunicorn
```

## Using Docker for the Deployment

You can containerize the application using Docker for better portability:

```bash
sudo docker build -t tod:ubuntu-22.04 .
sudo docker run -it -d --rm -p 8080:8080 --name tod tod:ubuntu-22.04
sudo docker exec -it tod bash
sudo docker stop tod
```

## Pros and Cons of This Deployment Approach

### Pros:
1. **Separation of Concerns:**
   - **Nginx** acts as a reverse proxy, handling client requests, static files, and forwarding dynamic content to Gunicorn.
   - **Gunicorn** manages multiple worker processes, making it more scalable and capable of handling multiple requests concurrently.
   
2. **Systemd for Process Management:**
   - Systemd allows for easy service management (start, stop, restart, enable on boot).
   - Ensures the application automatically restarts in case of failure.

3. **Performance:**
   - Nginx is known for its high performance and low memory footprint, making it ideal for production environments.
   - Gunicorn is lightweight and efficient in serving Python web apps.

4. **Security:**
   - Running the app behind Nginx ensures better security as Nginx handles SSL termination and can restrict direct access to Gunicorn.
   - Systemd ensures that services are started with the least privilege necessary (i.e., not running as root).

### Cons:
1. **Complexity in Setup:**
   - Setting up Nginx, Gunicorn, and Systemd together involves a fair amount of configuration. Each component has to be properly configured, and troubleshooting issues like permission errors or incorrect configurations can take time.

2. **Maintenance Overhead:**
   - Managing multiple services (Nginx, Gunicorn, Systemd) adds more maintenance tasks (e.g., keeping logs, ensuring services are running correctly).
   - Debugging issues across Nginx, Gunicorn, and Flask can be tricky, especially when configurations are not aligned properly.

3. **Not as Portable Without Docker:**
   - While Docker can containerize the entire setup for better portability, not using Docker means replicating the setup manually on different servers, which increases the chance of misconfiguration.

4. **Gunicorn Limitations:**
   - Gunicorn is better suited for lightweight applications. For more complex apps requiring WebSocket support or long-running connections, an alternative like uWSGI might be more appropriate.

---

## Links Section

- [Gunicorn Official Documentation](https://docs.gunicorn.org/en/stable/install.html)
- [Nginx PID Error Fix](https://bobcares.com/blog/failed-to-parse-pid-from-file-run-nginx-pid-invalid-argument/)
- [How to Serve Flask Applications with Gunicorn and Nginx](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-18-04)