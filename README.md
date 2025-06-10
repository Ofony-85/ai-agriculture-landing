# 🌿 AI in Agriculture – Project Landing Page

Welcome to the official landing page for my AltSchool, School of Engineering (Tinyuka, Semester 2) project: **The Future of AI in Agriculture**.

This web application is deployed on an AWS EC2 Ubuntu server using Node.js, Express, and Nginx as a reverse proxy.

---

## ✅ Steps to Provision the Server

1. **Launch EC2 Instance:**
   - Ubuntu 22.04 LTS
   - Enable HTTP (port 80) and SSH (port 22) in security group

2. **SSH into EC2:**
   ```bash
   chmod 400 OfonimeOffong_key.pem
   ssh -i "OfonimeOffong_key.pem" ubuntu@<your-ec2-public-ip>

**UPDATE PACKAGES**
sudo apt update && sudo apt upgrade -y

**Install Node.js and npm**
sudo apt install nodejs npm -y

**Install PM2**
sudo npm install -g pm2

✅ Setting Up Node.js & Express
**Initialize Node.js App:**
mkdir ai-agriculture && cd ai-agriculture
npm init -y

Install Express:
npm install express

**Create index.js:**
const express = require('express');
const app = express();
const port = 3000;

app.use(express.static('public'));

app.listen(port, () => {
  console.log(`🚀 Server is running at http://localhost:${port}`);
});

**Create public/index.html with your landing page content**.
**Start the App using PM2:**
pm2 start index.js
pm2 save
pm2 startup

**✅ Configure Nginx as Reverse Proxy
Install Nginx:**
sudo apt install nginx -y

**Configure the Default Site:**
sudo nano /etc/nginx/sites-available/default

**Replace the location / block with:**
server {
    listen 80;
    server_name your-ec2-public-ip;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}

**Restart Nginx:**
sudo nginx -t
sudo systemctl restart nginx

**✅ Screenshot of Landing Page**

**✅ Public IP / Domain**
🌐 http://34.201.116.173/


**✅ Tech Stack**
Node.js
Express.js
Nginx
AWS EC2 (Ubuntu)
PM2

**👨🏾‍💻 Author**
Ofonime Offong
AltSchool (School of Engineering) – Tinyuka24, Semester 2

