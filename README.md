# Installing

Ubuntu / Debian:

```shell
sudo apt-get install smokeping fcgiwrap nginx
```

# Smokeping with Nginx — configuration examples

Because links to images generates with /smokeping/, all configs use this path for static files and images.

## simple.conf

Very simple, but main page not in /smokeping/, main page is http://smokeping.example.com/cgi-bin/smokeping.cgi

## big.conf

Partialy used content of `/etc/nginx/fastcgi_params`, except of `SCRIPT_FILENAME`.

## best.conf

Like `big.conf`, but with redirect from wrong URLs to main page.
