# tutorial that would take you from a fresh Arch Linux server running on DigitalOcean to serving the demo document.

# It is important to update your system evertime you start
```bash
sudo pacman -Syu
```

# Install Nginx, this command install Nginx if not installed
```bash
sudo pacman -S nginx
```

# Install Vim, This installs the vim if not installed
```bash
sudo pacman -S vim
```

# Start Nginx
```bash
sudo systemctl start nginx
```

# Enable Nginx
```bash
sudo systemctl enable nginx
```

# You could also check the status of Nginx
```bash
sudo systemctl status nginx
```
# Now Nginx is up and running 

# Now create a new directory "/web/html/nginx-2420" that will act as your project root. Here all website documents will be stored
```bash
mkdir -p /web/html/nginx-2420
```
# -p is used create the directory even if path does not exist.





