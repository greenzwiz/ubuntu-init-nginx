ubuntu-init-nginx 
=================

**Description:** This is my custom nginx init script for ubuntu server 14.04.1 based on [JasonGiedymin's config](https://github.com/JasonGiedymin/nginx-init-ubuntu).

Installation and usage 
=================
**Note:** This script is intended for use with my nginx configuration files, which can be found [here](https://github.com/greenzwiz).

##### Install essentials.
```
apt-get install libpcre3-dev zlib1g-dev -y

apt-get install build-essential -y

apt-get install python-software-properties -y

apt-get install software-properties-common -y
```

##### Make downloads folder to store files. 
```
mkdir -p /usr/share/downloads

cd /usr/share/downloads
```

##### Download and extract nginx version 1.6.2.
```
wget http://nginx.org/download/nginx-1.6.2.tar.gz

tar -xvf nginx-1.6.2.tar.gz
```

##### Download and extract nginx headers more module.
```
wget https://github.com/openresty/headers-more-nginx-module/archive/v0.25.tar.gz

tar -xvf v0.25.tar.gz
```

##### Download and extract ngx_cache_purge module. 
```
wget https://github.com/FRiCKLE/ngx_cache_purge/archive/2.1.tar.gz

tar -xvf 2.1.tar.gz
```

##### Compile and install nginx.
```
cd nginx-1.6.2

./configure --prefix=/etc/nginx --pid-path=/var/run/nginx.pid --lock-path=/var/lock/nginx.lock --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --user=nginx --group=nginx --add-module=/usr/share/downloads/headers-more-nginx-module-0.25 --add-module=/usr/share/downloads/ngx_cache_purge-2.1

make && make install
```


