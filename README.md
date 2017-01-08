# docker-lineage-cicd

Docker microservice for LineageOS Continuous Integration and Continous Deployment

## Why

Because I always believe that even advanced technologies should be available to everyone. This is a tentative to offer everyone the possibility to build his own images of LineageOS, when he wants, how he wants. You don't have to wait anymore for build bots. No more scene drama. Just build and enjoy your favourite Android ROM.

## Why Docker?

Because I'm a big fan of isolating everything if possible. I don't want to reinstall my OS or triage with dirty packages, just because today I need somethng, and tomorrow I'll need something else.

## How it works

This docker will autobuild any device list given for a specified branch every midnight at 02:00 UTC. In the end, any built ZIP will be moved to the relative volume mapped directory to `/srv/out`.

## How to use

### Simple mode
build LineageOS for `hammerhead` with default settings
```
docker run \
    --restart=always \
    -d \
    -e "DEVICE_LIST=hammerhead" \
    -v "/home/user/ccache:/srv/ccache" \
    -v "/home/user/source:/srv/src" \
    -v "/home/user/zips:/srv/out" \
    julianxhokaxhiu/docker-lineage-cicd
```

### Advanced mode
build cm-13.0 LineageOS for `hammerhead` and `bullhead`
```
docker run \
    --restart=always \
    -d \
    -e "BRANCH_NAME=cm-13.0" \
    -e "DEVICE_LIST=hammerhead,bullhead" \
    -v "/home/user/ccache:/srv/ccache" \
    -v "/home/user/source:/srv/src" \
    -v "/home/user/zips:/srv/out" \
    julianxhokaxhiu/docker-lineage-cicd
```