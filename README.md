# who-to-run-react-nodejs-project-to-Nginx-with-Nginx

> first install pm2 with global command
```
sudo npm install pm2 -g
```
> add this file to nginx site avalible
in which we disable the root path so , run throw the pm2
also disable the defalut index files.

```ruby
server {

        listen 80;
        listen [::]:80;

        server_name www.test.ascend.com.sa test.ascend.com.sa;
#       server_name _;

#        root /var/www/admin/build;
#       index index.html index.htm index.nginx-debian.html;

     location / {
         proxy_pass http://localhost:3000;
         proxy_http_version 1.1;
         proxy_set_header Upgrade $http_upgrade;
         proxy_set_header Connection 'upgrade';
         proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
}
}
```
#GO TO THE PROJECT DIRECTORY THEN GO TO YOUR FRONTEND/BACKEND FOLDER
>run this on dev to configure / and check errors
```
npm run dev
```
