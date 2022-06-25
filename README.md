# Smokeping with Nginx

## Configuration examples

Because links to images generates with /smokeping/, all configs use this path for static files and images.

### simple.conf

Very simple, but main page not in /smokeping/, main page is http://smokeping.example.com/cgi-bin/smokeping.cgi

### big.conf

Partialy used content of `/etc/nginx/fastcgi_params`, except of `SCRIPT_FILENAME`.

### best.conf

Like `big.conf`, but with redirect from wrong URLs to main page.


## Installing

### Ubuntu / Debian

Note: `apache2-` argument is using here to force APT to not install `apache2` package, which is in _recommends_ list of `smokeping` package. It is also possible to use `--no-install-recommends`, but then other useful packages will not be installed automatically.

Replace here "smokeping.example.net" by your DNS name:

```shell
export MYSITENAME="smokeping.example.net"
sudo apt-get -V install smokeping apache2-
sudo apt-get -V install fcgiwrap nginx
wget "https://github.com/vazhnov/smokeping_nginx/raw/main/best.conf"
sed -i -- s/smokeping\.example\.com/${MYSITENAME}/g best.conf
sudo chown root: best.conf
sudo mv best.conf /etc/nginx/sites-available/${MYSITENAME}.conf
sudo ln -s "../sites-available/${MYSITENAME}.conf" "/etc/nginx/sites-enabled/${MYSITENAME}.conf"
sudo nginx -t
```

## Useful links

* [Nginx configurations for most popular CMS/CMF/Frameworks based on PHP](https://github.com/elasticweb/nginx-configs)
* [recipes](https://github.com/nginxinc/nginx-wiki/tree/master/source/start/topics/recipes) from [nginx-wiki](https://www.nginx.com/resources/wiki/)
* [examples](https://github.com/nginxinc/nginx-wiki/tree/master/source/start/topics/examples) from [nginx-wiki](https://www.nginx.com/resources/wiki/)

## Copyright

Distributed under MIT license.
