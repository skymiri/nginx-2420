# Generate service file
#/etc/systemd/system/hello-server.service .

#[Unit]
#Description=Hello Server

#[Service]
#ExecStart=/usr/bin/nginx

#[Install]
#WantedBy=multi-user.target

#start hello-server symbolic
#sudo systemctl enable hello-server
#sudo systemctl start hello-server

#/etc/nginx/sites-available/2420-file-server edit.

server {
    listen 80;

    servername ;

    location / {
        proxy_pass http://127.0.0.1:8080/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}

#check status of nginx 
sudo nginx -t
sudo systemctl restart nginx

#check 
curl http://http://143.198.229.89//hey
curl -X POST -H "Content-Type: application/json" \
  -d '{"message": "Hello from your server"}' \
  http://http://143.198.229.89//
