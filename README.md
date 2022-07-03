# who-to-run-react-nodejs-project-to-pm2-with-Nginx

> first install pm2 with global command
```
sudo npm install pm2 -g
```
> add this file to nginx site avalible
in which we disable the root path so , run throw the pm2
also disable the defalut index files.

# Nginx as a HTTP proxy [example = 1]
```ruby
server {

        listen 80;
        listen [::]:80;

        server_name www.xxxxx.com xxxx.com;
#       server_name _;

#        root /var/www/myproject/build;
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
# Nginx as a HTTP proxy [example = 2]
```ruby
upstream my_nodejs_upstream {
    server 127.0.0.1:3001;
    keepalive 64;
}

server {
        listen 80;
        listen [::]:80;
    
    server_name www.my-website.com;
   
    location / {
    	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real-IP $remote_addr;
    	proxy_set_header Host $http_host;
        
    	proxy_http_version 1.1;
    	proxy_set_header Upgrade $http_upgrade;
    	proxy_set_header Connection "upgrade";
        
    	proxy_pass http://my_nodejs_upstream/;
    	proxy_redirect off;
    	proxy_read_timeout 240s;
    }
}
```
[LINK]: https://pm2.keymetrics.io/docs/tutorials/pm2-nginx-production-setup


# GO TO THE PROJECT DIRECTORY THEN GO TO YOUR FRONTEND/BACKEND FOLDER

>run this on dev to configure / and check errors
```
npm run dev
>Have to create build with npm :
npm run build
```
>Delete current pm2 instance
stop and delete a process from the list
```
pm2 delete app
```
Run in frontEnd folder
```
pm2 start npm --name "myfrontend" -- start
```
# NOTE
if you not build the npm ,then run this command 
```
pm2 start node.js --max-memory-restart=50G -i 0 -f
```
Note : run above command in (public_html)project folder where node/react are deplyed.

Routine
-------------------------
>Once setup your process list, every actions are done with the process name.

#kill the process but keep it in the process list
```
pm2 stop app
```
#start the process again
```
pm2 start app
```
#both stop and start
```
pm2 restart app
```
Save your process list
----------------------------------

#save your list in hard disk memory
```
pm2 save
```
#resurrect your list previously saved
```
pm2 resurrect
```

Local Monitoring
--------------------
```
pm2 monit
```




done
Visit :https://devstudioonline.com/article/deploy-nextjs-app-with-nginx-and-pm2-on-linux-ubuntu
Visit :https://pm2.io/docs/runtime/guide/process-management/
>for further problem in CROS css style-sheet
Visit :https://stackoverflow.com/questions/57715058/get-css-from-different-domain-blocked-by-cors-policy-no-access-control-allow-o
