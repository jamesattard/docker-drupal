# About

Drupal running on Docker behind an Nginx proxy and accessible through
http://drupal.localhost/.

# Requirements

First make sure you have a local DNS Server that is able to proxy local requests
correctly. If you are using OSX or Linux, I suggest to use dnsmasq. The
following is the process to setup dnsmasq on OSX:

```sh
$ brew install dnsmasq
```

Update "/usr/local/etc/dnsmasq.conf" as follows:

```sh
listen-address=127.0.0.1
port=35353
address=/.localhost/127.0.0.1
```

Start dnsmasq as a service:

```sh
$ brew service start dnsmasq
```

Finally, create a new file, /etc/resolver/localhost, to resolve all .localhost
DNS requests:

```sh
port 35353
nameserver 127.0.0.1
```

If you do not want to use dnsmasq, just update your /etc/hosts file so that
http://drupal.localhost points to your host.

# Installation

```sh
$ git clone https://github.com/jamesattard/docker-drupal.git
$ cd docker-drupal
$ docker-compose up
```

# Usage

Just point your browser to http://drupal.localhost/

# Notes

When configuring Drupal for the first time installation make sure that the
database name, database username and hosts are set correctly (postgres by
default). Password can be set in docker file.
