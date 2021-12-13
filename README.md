# localtunnel PI

> A Docker compose to run [localtunnel](https://localtunnel.me) on a Raspberry PI (Docker platform linux/arm/v7).

localtunnel exposes your localhost to the world for easy testing and sharing! No need to mess with DNS or deploy just to have others test out your changes.

If you are just looking for the localtunnel client CLI, see ([https://github.com/localtunnel/localtunnel](https://github.com/localtunnel/localtunnel)).

## Requirements

In order to run your own localtunnel server you need to :

* Have DNS entries for your `domain.tld` and `*.domain.tld` (or `sub.domain.tld` and `*.sub.domain.tld`).
* Have a server which can accept incoming TCP connections for any non-root TCP port (i.e. ports over 1000).

The above are important as the client will ask the server for a subdomain under a particular domain. The server will listen on any OS-assigned TCP port for client connections.

## Set up environment

Copy `.env.example` as `.env` and replace `LOCALTUNNEL_DOMAIN` environment variable value with your own domain.

## SSL certificate

Form `nginx/ssl` folder, use `openssl` to generate your SSL certificate and key :

```
openssl req -x509 -nodes -days 365 -newkey rsa:4096 -sha256 -keyout server.key -out server.crt
```

## Start localtunnel server

```
docker-compose up -d
```
