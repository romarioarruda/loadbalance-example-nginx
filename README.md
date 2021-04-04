
on file:
```
$ vim /etc/nginx/conf.d/default.conf
```

config load_balance:

```
upstream nodes {
    server node1;
    server node2;
}

config server

server {
    listen      80;
    listen [::]:80;
    server_name localhost;

    location / {
        proxy_pass http://nodes; # using loadbalance
        proxy_set_header X-Real-IP $remote_addr;
    }

    access_log /var/log/nginx/nginx-access.log;
}
```