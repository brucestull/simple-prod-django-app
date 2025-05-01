# simple-prod-django-app

Simple production-ready Django app on WSL Ubuntu example.

- [Basic commands for WSL](https://learn.microsoft.com/en-us/windows/wsl/basic-commands)
- [Django Production Setup WSL - Shared](https://chatgpt.com/share/6812ca8e-cee4-8002-a4bd-bed4f16618fd)
- [Django Production Setup WSL - Private](https://chatgpt.com/c/6812ca20-ed3c-8002-9903-ba87166d778e)

Absolutely — here’s a full, **simple Django app setup** with production configurations using:

- **Gunicorn** (app server)
- **Supervisor** (process monitor)
- **Nginx** (reverse proxy)
- **PostgreSQL** (optional but production-preferred DB)
- **Static file handling**
- Designed for **WSL Ubuntu**, but easily portable to real Linux servers.

---

## ✅ 1. Django App Creation (WSL Ubuntu)
```bash
sudo apt update && sudo apt install python3-venv python3-pip -y
mkdir ~/myproject && cd ~/myproject
python3 -m venv venv
source venv/bin/activate
pip install django gunicorn psycopg2-binary
django-admin startproject config .
```

---

## ✅ 2. Settings Adjustments (`config/settings.py`)

```python
# Add or modify:
ALLOWED_HOSTS = ['localhost', '127.0.0.1']  # Add your server IP/domain later
DEBUG = False

STATIC_URL = '/static/'
STATIC_ROOT = BASE_DIR / 'static'

# Optionally configure PostgreSQL
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```

---

## ✅ 3. Collect Static Files

```bash
python manage.py migrate
python manage.py collectstatic
```

---

## ✅ 4. Gunicorn Test

```bash
gunicorn config.wsgi:application --bind 127.0.0.1:8000
```

---

## ✅ 5. Supervisor Configuration

Install Supervisor:
```bash
sudo apt install supervisor
```

Create config:
```bash
sudo nano /etc/supervisor/conf.d/myproject.conf
```

Paste:
```ini
[program:myproject]
directory=/home/youruser/myproject
command=/home/youruser/myproject/venv/bin/gunicorn config.wsgi:application --workers 3 --bind 127.0.0.1:8000
autostart=true
autorestart=true
stderr_logfile=/var/log/myproject.err.log
stdout_logfile=/var/log/myproject.out.log
user=youruser
environment=PATH="/home/youruser/myproject/venv/bin"
```

Then:
```bash
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl start myproject
```

---

## ✅ 6. Nginx Reverse Proxy

Install:
```bash
sudo apt install nginx
```

Configure:
```bash
sudo nano /etc/nginx/sites-available/myproject
```

Paste:
```nginx
server {
    listen 80;
    server_name localhost;

    location = /favicon.ico { access_log off; log_not_found off; }
    location /static/ {
        root /home/youruser/myproject;
    }

    location / {
        include proxy_params;
        proxy_pass http://127.0.0.1:8000;
    }
}
```

Enable site:
```bash
sudo ln -s /etc/nginx/sites-available/myproject /etc/nginx/sites-enabled
sudo nginx -t
sudo systemctl restart nginx
```

---

## ✅ 7. File Permissions and Firewall (optional)

```bash
sudo chown -R www-data:www-data ~/myproject/static
```

(You don’t need `ufw` for WSL, but for real servers: `sudo ufw allow 'Nginx Full'`)

---

## ✅ 8. Test it

Visit `http://localhost` on your browser in Windows. You should see the Django welcome page (if static files are collected and Nginx is passing through correctly).

---

Would you like me to zip up a working project directory for you or generate a PDF guide?
