Ansible Role for DIANA in Docker
===================================

[![Build Status](https://travis-ci.org/derekmerck/ansible-diana-docker.svg?branch=master)](https://travis-ci.org/derekmerck/ansible-diana-docker)

Derek Merck  
<derek_merck@brown.edu>  
Rhode Island Hospital and Brown University  
Providence, RI  

Configure and run a [DIANA](https://github.com/derekmerck/DIANA) DICOM handler node in a Docker container.


Dependencies
------------

### Galaxy Roles

- [geerlingguy.docker](https://github.com/geerlingguy/ansible-role-docker) to setup the docker environment
- [geerlingguy.pip](https://github.com/geerlingguy/ansible-role-pip) to install Python reqs
- [derekmerck.redis-docker](https://github.com/derekmerck/ansible-redis-docker) for Redis backend


### Remote Node

- [Docker][]
- [docker-py][]

[Docker]: https://www.docker.com
[docker-py]: https://docker-py.readthedocs.io


Role Variables
--------------

### Docker Image and Tag

Set the repo to clone to build the Snappass image.

- https://github.com/pinterest/snappass - official repo (uses branch "master")
- https://github.com/jameswthorne/snappass - fork that publishes an api (uses branch "api")

```yaml
snappass_repo_url: https://github.com/pinterest/snappass
```

### Docker Container Configuration

Uses Flask and Flask default port.

```yaml
snappass_container_name:        snappass
snappass_port:                  5000
```

### Redis Backend Configuration

```yaml
snappass_redis_container_name:  redis
snappass_redis_port:            6379
snappass_redis_password:        "passw0rd!"
snappass_redis_db:              0
```


Example Playbook
----------------

```yaml
- hosts: snappass_server
  roles:
     - derekmerck.snappass_docker
```


License
-------

MIT