# Sentry On-Premise

Based on [getsentry/onpremise](https://github.com/getsentry/onpremise).

Unofficial bootstrap for running your own [Sentry](https://getsentry.com/) with [Docker](https://www.docker.com/) and SSL using [LetsEncrypt](https://letsencrypt.org).

## Requirements

 * Docker 1.10.0+
 * Compose 1.6.0+ _(optional)_

## Deployment

```sh 
docker-compose run --rm base config generate-secret-key
vi docker-compose.yml # add SENTRY_SECRET_KEY, VIRTUAL_HOST and LETSENCRYPT_EMAIL
docker-compose up -d redis postgres memcached smtp
docker-compose run --rm web upgrade
docker-compose up -d
curl https://localhost
```

## Resources

 * [Documentation](https://docs.getsentry.com/on-premise/server/installation/docker/)
 * [Bug Tracker](https://github.com/meatcar/onpremise)
 * [IRC](irc://chat.freenode.net/sentry) (chat.freenode.net, #sentry)
