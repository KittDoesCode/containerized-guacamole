# Apache Guacamole in a Container with TLS

This Docker Compose setup makes it very easy (only two cli commands) to run [Apache Guacamole](https://guacamole.incubator.apache.org/) behind a NGINX reverse proxy TLS secured with Let's Encrypt.

*Although this repo is 3 years old it still works and is up to date as latest images are used.*

## Unique Features

* Unlike other solutions this setup is much simpler to setup and is inline with docker/docker-compse best practice.
* Utilize oznu/guacamole combined Guacamole container.
* Automatically created and configured Nginx Reverse Proxy in front of the Guacamole Service.
* TLS encrypted traffic with Let's Encrypt for your public domain.
* Minimal configuration of only *two* mandatory environment variables.

## Run

Before you start the service, define three mandatory variables.
The easiest way is to create a `.env` file in your working directory eg.:

### Step 1 - Define your Domain:

```ini
cat > .env <<EOF
VIRTUAL_HOST=workshop.domain.com
LETSENCRYPT_EMAIL=user@domain.com
EOF
```

### Step 2 - Start Guacamole and other Services:

Finally we can start Guacamole.

```sh
docker-compose up -d
```

Now go to your application https://workshop.domain.com and login as guacadmin/guacadmin. 
Don't forget to change the password in the next step. You'll be prompted to set up 2FA
upon login as well.
