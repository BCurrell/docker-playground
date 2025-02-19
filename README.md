# Docker Playground

Playground using Docker to test different applications locally

## Docker Configuration

Here are a few changes I recommend making to Docker, and why.

Merge this JSON objects into `/etc/docker/daemon.json`. Any changes you make to this file will require a restart of any docker compose stacks and the docker daemon itself. Make sure to do `docker compose down; systemctl restart docker; docker compose up` (or relevant commands for your setup).

### Default Address Pools

By default, docker will create a network with a /16 subnet within 172.16.0.0/12. This is ridiculously large, and if you run multiple compose stacks that are all setting up private networks, you will soon "run out" of address space. In order to avoid this, you can adjust the defualt address pools. My settings below will allocate a /24 from a subnet of 172.16.0.0/12, broken up into /16s. This is still a ridiculous number, but it gives you 1,280 unique networks.

```json
{
  "default-address-pools": [
    {
      "base": "172.16.0.0/16",
      "size": 24
    },
    {
      "base": "172.17.0.0/16",
      "size": 24
    },
    {
      "base": "172.18.0.0/16",
      "size": 24
    },
    {
      "base": "172.19.0.0/16",
      "size": 24
    },
    {
      "base": "172.20.0.0/16",
      "size": 24
    }
  ]
}
```
