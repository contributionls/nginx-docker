# Common Nginx docker-compose

this docker configuration comes from [buchdag/letsencrypt-nginx-proxy-companion-compose](https://github.com/buchdag/letsencrypt-nginx-proxy-companion-compose) ,based [JrCs/docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion),it's perfect for every reverse pass with virtual host docker.

## Get started

### Run nginx

For first time, you should create a specific docker bridge network for this nginx docker container(In order not to affect other containers):

```bash
docker network create nginx-proxy
```

then,just run:

```bash
docker-compose up -d
```

### Run any other containers

So, if your other container want to be proxy with nginx,you just add the follow enviroment variables;

```bash
VIRTUAL_HOST=subdomain.yourdomain.tld
LETSENCRYPT_HOST=subdomain.yourdomain.tld
```

and join the specific network(In order not to affect other containers):

```bash
networks:
  default:
    external:
      name: nginx-proxy
```
