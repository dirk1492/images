
HAProxy 1.6 base image using ubuntu-slim-arm64

This is a arm64 port of the gcr.io/google_containers/haproxy image.

What is HAProxy?
HAProxy is a free, very fast and reliable solution offering high availability, load balancing, and proxying for TCP and HTTP-based applications.

**How to use this image:**
This image does provides a default configuration file with no backend servers.

*Using docker*
```
$ docker run -v /some/haproxy.cfg:/etc/haproxy/haproxy.cfg:ro dil001/haproxy-arm64:0.5
```

*Creating a pod*
```
$ kubectl create -f ./pod.yaml
```
