# `home-networking`

Configuration and tools to manage my home network.

It will mostly be responsible for running our [Unifi
controller](https://help.ui.com/hc/en-us/articles/360012192813-Introduction-to-UniFi).
It will also expose the Unifi controller to Prometheus for our [home
monitoring system](https://github.com/SteveMarshall/home-monitoring/).

## Getting started

Everything is put together using [Docker
Compose](https://docs.docker.com/compose/), so you should just be able
to run:

```
docker compose up
```

Then open:

- [Unifi console](http://localhost:8443/)

### Can't use Docker Compose?

For environments where Docker Compose won't work (for example, because
you're running a really old Mac as a server), you can run it in Vagrant
with Virtualbox like so:

```
vagrant up
```
