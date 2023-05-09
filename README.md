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

## Running in the background on macOS

If you want to run this networking system all the time on a Mac that
operates as a server, the easiest thing to do is launch the Vagrant VM
as a macOS LaunchAgent.

To do that, you'll need to:

1. [Enable passwordless NFS mounting](https://developer.hashicorp.com/vagrant/docs/synced-folders/nfs#root-privilege-requirement)
2. Install the LaunchAgent (assuming you're in this directory):

```shell
ln -s `pwd`/macOS-LaunchAgent.plist ~/Library/LaunchAgents/com.stevemarshall.StartHomeNetworking.plist
launchctl load ~/Library/LaunchAgents/com.stevemarshall.StartHomeNetworking.plist
```

NB: We're currently assuming your `vagrant` is installed in
`/opt/vagrant/bin`, which mine is on the target machine, but isn't on
another. I'm not sure how to make LaunchAgents handle that for now.
