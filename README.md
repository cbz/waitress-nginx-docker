# gunicorn-nginx
**Docker** image with **waitress** and **nginx** for web applications
written in the latest stable version of **Python** (currently 3.7).

## Description

This [**Docker**](https://www.docker.com/) image will allow creation of
[**Python**](https://www.python.org/) web applications running under 
[**waitress**](https://github.com/Pylons/waitress) and [**NGinx**](https://www.nginx.com/).

Built on the alpine branch of the official python docker distribution
it is intended as a lightweight container that implements signal 
handling correctly (via runit)and tracks the latest release of 
python for development and occasional deployment.

It includes the postgres and mariadb libraries so that python database
libraries can be installed - these can be stripped out for a smaller image.

# Customization

### Custom app directory

By default the container expects the app to be in a directory '/app'. This can
be overridden with the `APPDIR` environment variable

```Dockerfile

ENV APPDIR /application
```

### Custom app name

By default an app called main:app in the directory `/app` is executed
this can be specified and overridden with the `MODULE_APP` 
environment variable.

```Dockerfile

ENV MODULE_APP myapp:app
```

### Custom number of gunicorn workers

By default the container will launch a number of waitress threads equal to 
_cpus + 1_ this can be overriden using the `CONCURRENCY` environment
variable.

```Dockerfile

ENV CONCURRENCY 4
```

### Custom maximum upload size

In this image, Nginx is configure to allow a maximum upload file size
of 1M. 

This can be specified and over-ridden using the variable `NGINX_MAX_UPLOAD`

```Dockerfile

ENV NGINX_MAX_UPLOAD 2m
```

## License

This project is licensed under the terms of the Apache license.

