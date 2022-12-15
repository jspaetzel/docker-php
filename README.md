# Docker w/ PHP

This is a bare-bones project to show how to use Docker with Apache, PHP, and a self-signed SSL cert via Traefik. This repo is also contains the minimal configuration for xdebug 3!

# Quick Start

1. Add `example.test` to your hosts file
```
127.0.0.1 example.test
```

2. Gen certs
```
mkcert example.test
mv example.*.pem docker/traefik/certificates/
```

3. See website https://example.test