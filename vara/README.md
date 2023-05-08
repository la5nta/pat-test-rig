# Caveats

## Missing installation

I was unable to automate the process of installing all Windows dependencies
required to run VARA. Consequently, you need to prepared .wine/ installation
archived as `vara.tar`. The archive can not be included in the repo due to
licensing issues.

## Subsequent TCP connections fails

It seems the TCP ports are not released after the connection is closed. The
workaround is restart all containers.

## xvfb is left in a bad state

The headless X server (xvfb) is left in a bad state when stopping the
containers. The workaround is to delete the containers and re-create each time.

```
docker-compose rm -s
docker-compose up
```
