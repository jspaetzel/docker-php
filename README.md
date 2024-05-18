# Docker w/ PHP

This is a bare-bones project to show how to use Docker with Apache, PHP, and a self-signed SSL cert. This repo also contains some minimal configuration for using xdebug 3 with docker!

# Quick Start

1. Add `example.test` to your hosts file
```
127.0.0.1 example.test
```

2. Gen certs
```
mkcert example.test
mv example.*.pem docker/certificates/
```

3. See website https://example.test
