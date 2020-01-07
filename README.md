# Account.Ichi

![preview.png](https://i.loli.net/2020/01/07/HEUlBt8zOowqAjW.png)

## Wha-hh?
A general template of user account center. Okay, fine! It's just something I coded but got cut...
It's halfway done, just for reference.

## Inspiration
Visual design inspired by ***Microsoft***:  
- [login.live.com](https://login.live.com)
- [account.microsoft.com](https://account.microsoft.com)

## Components
- Spectre CSS
- Flight PHP Framework
- JQuery

## Configuration

### Database

Create a file and paste above content, then fill out:
```
[app]
debug=true

[database]
username=
password=
database=
host=localhost
```

### Vhost (for Nginx)

Remember to set the root folder of your website to ***\public*** folder for **security reason**.
```
server {
        listen       80;
        server_name  account.ichi.io ;
        root   "path\to\folder\Account.Ichi\public";
        location / {
            index  index.html index.htm index.php;
            try_files  $uri /index.php;
        }
        location ~ \.php(.*)$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_split_path_info  ^((?U).+\.php)(/?.+)$;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            fastcgi_param  PATH_INFO  $fastcgi_path_info;
            fastcgi_param  PATH_TRANSLATED  $document_root$fastcgi_path_info;
            include        fastcgi_params;
        }
}
```
