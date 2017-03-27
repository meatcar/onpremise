# Sentry On-Premise

Based on [getsentry/onpremise](https://github.com/getsentry/onpremise).

Unofficial bootstrap for running your own [Sentry](https://getsentry.com/) with [Docker](https://www.docker.com/) and SSL using [LetsEncrypt](https://letsencrypt.org).

## Requirements

 * Docker 1.10.0+
 * Compose 1.6.0+ _(optional)_

## Up and Running

Assuming you've just cloned this repository, the following steps
will get you up and running in no time!

There may need to be modifications to the included `docker-compose.yml` file to accommodate your needs or your environment. These instructions are a guideline for what you should generally do.

1. `mkdir -p data/{sentry,postgres}` - Make our local database and sentry config directories.
    This directory is bind-mounted with postgres so you don't lose state!
2. `docker-compose run --rm base config generate-secret-key` - Generate a secret key.
    Add it to `docker-compose.yml` in `base` as `SENTRY_SECRET_KEY`.
    Add `VIRTUAL_HOST` and `LETSENCRYPT_EMAIL`.
3. `docker-compose up -d redis postgres memcached smtp`.
4. `docker-compose run --rm web upgrade` - Build the database.
    Use the interactive prompts to create a user account.
5. `docker-compose up -d` - Lift all services (detached/background mode).
6. Access your instance at `localhost`!

Note that as long as you have your database bind-mounted, you should
be fine stopping and removing the containers without worry.

## Resources

 * [Documentation](https://docs.getsentry.com/on-premise/server/installation/docker/)
 * [Bug Tracker](https://github.com/meatcar/onpremise)
 * [Forums](https://forum.sentry.io/c/on-premise)
 * [IRC](irc://chat.freenode.net/sentry) (chat.freenode.net, #sentry)
