![active](http://img.shields.io/badge/status-active-green.png)

# modern.IE VMs with Vagrant and Virtual Box

## Prerequisites

### VirtualBox

```
brew cask install virtualbox
```

### Vagrant

```
brew cask install vagrant
```

```
vagrant plugin install vagrant-vbguest
```

## How to use

### Start the VMs

You can start any version of IE you'd like with just a simple command:

```sh
$ vagrant up ie11-win81 # or ie11-win7, msedge-win10
```

### Accessing Applications

Once you spin up your VM, you can access `localhost` on your host machine (macOS) via `10.0.2.2`.

```
http://10.0.2.2:8087
```

## Caviats

You may or may not get hot reload errors when running the web apps and accessing via Windows. Please disable hot reloading when running `yarn run customer` etc...
