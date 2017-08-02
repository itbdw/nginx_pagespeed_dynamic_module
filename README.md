# nginx_pagespeed_dynamic_module
Compiled Nginx Pagespeed Dynamic Module Binary Files. ngx_pagespeed.so

## What is this

Just a collection of pagespeed dynamic module builded file for nginx.


## How to use

* Copy the ngx_pagespeed.so with the right nginx version. (run `nginx -v` on your server to get nginx version)

* Load the module for your nginx.  

* Enable Pagespeed 

add to http or server block
```
pagespeed on;

# Needs to exist and be writable by nginx.  Use tmpfs for best performance.
pagespeed FileCachePath /var/ngx_pagespeed_cache;
```

add to server block
```
# Ensure requests for pagespeed optimized resources go to the pagespeed handler
# and no extraneous headers get set.
location ~ "\.pagespeed\.([a-z]\.)?[a-z]{2}\.[^.]{10}\.[^.]+" {
  add_header "" "";
}
location ~ "^/pagespeed_static/" { }
location ~ "^/ngx_pagespeed_beacon$" { }
```


## Links

[Pagespeed](https://github.com/pagespeed/ngx_pagespeed)

