# fttp-local-file-server-sharing-centre--arch-linux
Certainly, I can explain how to set up file sharing servers on Arch Linux. The process is similar, but with some Arch-specific commands and package names. I'll cover both FTP and HTTP server setup for Arch:

1. Setting up an FTP server on Arch:



a) Install vsftpd:
```
sudo pacman -S vsftpd
```

b) Edit the configuration file:
```
sudo nano /etc/vsftpd.conf
```

c) Ensure these lines are uncommented or add them:
```
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES
allow_writeable_chroot=YES
```

d) Start and enable the vsftpd service:
```
sudo systemctl start vsftpd
sudo systemctl enable vsftpd
```

e) If you're using ufw firewall, open the FTP port:
```
sudo ufw allow ftp
```

2. Setting up an HTTP server on Arch:

For a simple HTTP server, you can use Python's built-in http.server module (Python is typically pre-installed on Arch):

a) Navigate to the directory you want to share:
```
cd /path/to/your/directory
```

b) Start the Python HTTP server:
```
python -m http.server 8000
```

c) If you're using ufw firewall, open port 8000:
```
sudo ufw allow 8000
```

To access your shared files:

- For FTP: Use an FTP client and connect to ftp://your_arch_ip
- For HTTP: Open a web browser and go to http://your_arch_ip:8000

Replace "your_arch_ip" with your actual local IP address.

If you prefer a more robust HTTP server, you could install and configure Nginx:

a) Install Nginx:
```
sudo pacman -S nginx
```

b) Start and enable Nginx:
```
sudo systemctl start nginx
sudo systemctl enable nginx
```

c) Configure Nginx to serve your directory by editing /etc/nginx/nginx.conf

d) Open port 80 if using ufw:
```
sudo ufw allow http
```

Would you like more details on any part of these setups, or information on how to configure Nginx for file sharing?
