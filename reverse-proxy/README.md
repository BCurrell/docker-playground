# Reverse Proxy

Reverse proxy to access any containers with hostname / HTTP(S)

Anything that gets configured with a reverse proxy entry will need some sort of DNS entry to send the FQDN to the proxy. If this is hosted publicly, you can just point example.domain.tld to the public address of the container host. Alternatively, you need to add the entries to a local DNS server or `/etc/hosts`, pointing to localhost.

Example:

```none
127.0.0.1	llm.docker.internal
```
