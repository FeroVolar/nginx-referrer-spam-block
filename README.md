# nginx-referrer-spam-block
Easy way to block **Crawler Referrer Spam** on NGINX web server

* create file `/etc/nginx/blacklist.conf` with content from this repo
* include the file the the `http` block of your `/etc/nginx/nginx.conf` like this:
```
  http {
  # ...

    include blacklist.conf;

  # ...

  }
```
* add conditions to the sites, for which, you want to block referer spam bots for example `/etc/nginx/sites-enabled/default`
```
  server {
    # ...

    if ($bad_referer) {
      return 444;
    }

    # ...
  }
```
* restart you NGINX server
