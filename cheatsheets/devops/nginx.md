- `tail -f /var/log/nginx/error.log` -- for viewing error logs in nginx


### Django setup cheat sheet

nginx
```
user www-data;
worker_processes auto;

pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
  worker_connections 768;
  # multi_accept on;
}

http {

  upstream test_server {
    server unix:/var/www/html/demirantay/run/gunicorn.sock fail_timeout=10s;
  }
	
  server {
    include  /etc/nginx/mime.types;
    server_name  www.getdemir.com getdemir.com;
		
    client_max_body_size 4G;
		
    # access_log /var/www/test/logs/nginx-access.log;
    # error_log /var/www/test/logs/nginx-error.log warn;
		
    location /static/ {
      autoindex on;
      alias /var/www/html/demirantay/staticfiles/;
    }
    
    location /media/ {
      autoindex on;
      alias /var/www/html/demirantay/media/;
    }
    
    location / {
    	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    	proxy_set_header Host $http_host;
    	proxy_redirect off;
    	
    	if (!-f $request_filename) {
    	  proxy_pass http://test_server;
    	  break;
    	}
    	
    }
		  
  }

}
```
django static files:
```python
# Static

STATIC_URL = '/static/'
STATICFILES_DIRS = (os.path.join(BASE_DIR, "static"),)
STATIC_ROOT = os.path.join(BASE_DIR, "staticfiles")

MEDIA_URL = "/media/"
MEDIA_ROOT = os.path.join(BASE_DIR, "media")
```