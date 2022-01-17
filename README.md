# who-to-run-react-nodejs-project-to-pm2-with-Nginx

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
====================================================================

Have to create build with npm :
```
npm run build
```
>Delete current pm2 instance
stop and delete a process from the list
```
pm2 delete app
```
Run in frontEndNestJs folder
```
pm2 start npm --name "ascendportal" -- start
```
Routine
-------------------------
>Once setup your process list, every actions are done with the process name.

# kill the process but keep it in the process list
```
pm2 stop app
```
# start the process again
```
pm2 start app
```
# both stop and start
```
pm2 restart app
```
Save your process list
----------------------------------

# save your list in hard disk memory
```
pm2 save
```
# resurrect your list previously saved
```
pm2 resurrect
```

Local Monitoring
--------------------
```
pm2 monit
```












done
Visit https://devstudioonline.com/article/deploy-nextjs-app-with-nginx-and-pm2-on-linux-ubuntu
