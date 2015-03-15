# ZG Boot2Docker Vagrant VM

This Vagrant VM is meant to act as Proxy VM for other Vagrant based Docker setups.

Currently running version **1.5.0** of Docker

## Getting Started

1. Pull down the repo to `~/Workspace/docker/vagrant`

    **NOTE:** It is important that you clone to this folder since this path will be referecned in other ZG Docker based projects.

2. Run `vagrant up` inside cloned directory
3. Modify `/etc/hosts` file with the following lines

    ```
    127.0.0.1 boot2docker
    192.168.100.200 docker.local
    ```

4. Add the following to you shell profile

    ```
    # Docker
    export DOCKER_CERT_PATH=$HOME/Workspace/docker/vagrant/tls
    export DOCKER_HOST=tcp://boot2docker:2376
    export DOCKER_TLS_VERIFY=1
    export DOCKER_HOST_VAGRANT_FILE=$HOME/Workspace/docker/vagrant/Vagrantfile
    export DOCKER_HOST_VAGRANT_NAME="zg-docker-host"
    ```

5. Once you have a Docker client installed on your host (see below) you should be able to run `docker ps` and get a positive output

## Install Docker client on your host

You will want to be able to interact with this Docker host via the `docker` client on your host machine.

### OSX

Install via [Homebrew](http://brew.sh/).

```
brew install docker
```

## Known Issues

### `vagrant reload`

Something is wonky with our base box. If you run `vagrant reload` on on of your Docker projects, you might get an error. This error is harmeless, and if you just run `vagrant up` right after it, all will be well.

If you want to avoid this error, just run `vagrant destroy` then `vagrant up` to avoid it.