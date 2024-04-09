# tutorial for adding a firewall using UFW and a reverse proxy server to the backend included below.(Assuming completed part 1)

# It is important to update your system evertime you start
```bash
sudo pacman -Syu
```

# Now lets install ufw using pacman
```bash
sudo pacman -S ufw
```

# Now you should transfer the hello-server file from your system to your droplet using the following code.
# Replace user with your username, ip-address with your ip-address, and path with the path where your hello-server file is
```
sftp -i ~/.ssh/do-key user@ip-address
put <path>
```

# Now move this file to a logical location
```bash
sudo mv ~/hello-server /usr/local/bin/hello-server
```

# Now create new service file
```bash
sudo vim /etc/systemd/system/hello-server.service
```

# add this to your service file
```bash
[Unit]
Description=Hello-Server-backend Service
After=network.target

[Service]
ExecStart=/usr/local/bin/hello-server # location of your binary backend file
Restart=always # this will automatically restart

[Install]
WantedBy=multi-user.target
```

# start and enable the service
```bash
sudo systemctl start hello-server
sudo systemctl enable hello-server
```

# now edit nginx server block, add reverse proxy to backend
```bash
sudo vim /etc/nginx/sites-available/nginx-2420.conf
```
# add the following to end of your file you created in part 1
```bash
location /hey {
    proxy_pass http://127.0.0.1:8080;
}

location /echo {
    proxy_pass http://127.0.0.1:8080;
}
```

# test configuration 
```bash
sudo nginx -t
```
# restart nginx now
```bash
sudo systemctl restart nginx
```

# using ufw allow ssh,http,https
```bash
sudo ufw allow http
sudo ufw allow https
sudo ufw allow ssh
```

# enable ufw
```bash
sudo ufw enable
```



