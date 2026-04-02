
worklog 

/ deployed

/backend

pm2 start ./src/app.js --name worklog-backend
pm2 startup

### Generic example 
sudo env PATH=$PATH:/usr/bin /usr/lib/node_modules/pm2/bin/pm2 startup systemd -u ubuntu --hp /home/ubuntu

### To be used
``` bash
sudo env PATH=$PATH:/usr/bin /usr/local/bin/pm2 startup systemd -u ubuntu --hp /home/ubuntu   
```

sudo nano /etc/nginx/sites-available/worklog-app

sudo ln -s /etc/nginx/sites-available/worklog-app /etc/nginx/sites-enabled1

pm2 show worklog-backend


/frontend
/pnpm run build

check nginx : systemctl status nginx





example nginx server
```

server {
    listen 80;
    server_name your_ec2_ip;

    # Frontend (e.g., React app)
    location / {
        proxy_pass http://localhost:frontend_port;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }

    # Backend API (e.g., Node.js/Express)
    location /api/ {
        proxy_pass http://localhost:backend_port/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }
}   
```

current nginx server
```

server {
    # Listen on port 80 (Standard HTTP)
    listen 80;
    listen [::]:80;

    # Your specific public IP address
    server_name 54.89.114.17; 

    
    location /api/ {
        # Forward all requests to your app running on port 4173
        proxy_pass http://localhost:8090;
        
        # Enable WebSocket support (crucial for modern web frameworks)
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        
        # Pass standard headers to the application
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
    location / {
        # Forward all requests to your app running on port 4173
        proxy_pass http://localhost:4173;
        
        # Enable WebSocket support (crucial for modern web frameworks)
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        
        # Pass standard headers to the application
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```