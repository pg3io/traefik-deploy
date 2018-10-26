![version](https://img.shields.io/badge/version-v1.0-orange.svg)
[![Build Status](https://travis-ci.com/adri1s/traefik-deploy.svg?branch=master)](https://travis-ci.com/adri1s/traefik-deploy)
[![Twitter](https://img.shields.io/twitter/follow/pg3io.svg?style=social)](https://twitter.com/intent/follow?screen_name=pg3io)

-----

# Two methods to deploy reverse-proxy docker traefik with ansible on docker swarm
1. Ansible with module docker_swarm_service for only one docker service [ref](https://docs.ansible.com/ansible/devel/modules/docker_swarm_service_module.html)

2. Ansible 2.8 (devel version) with module docker_stack and docker-compose.yml for docker stack [ref](https://docs.ansible.com/ansible/devel/modules/docker_stack_module.html)

## Module docker_swarm_service
### Requirements
* Ansible 2.7

```
pip install ansible==2.7
```

### Deploy traefik
* update hosts file with your \<IP_DOCKER_MANAGER> and launch the following command :

```
ansible-playbook docker-traefik.yml -i hosts
```

## Module docker_stack
### Requirements

* Ansible 2.8

```
pip install git+git://github.com/ansible/ansible.git@devel --upgrade
```

### Deploy traefik
* update hosts file with your \<IP_DOCKER_MANAGER> and launch the following command :

```
ansible-playbook docker-traefik-devel.yml -i hosts
```

# Access to traefik dashboard

```
http://<IP_DOCKER_MANAGER>:8080/dashboard
```


# Validation of traefik workflow

Try to launch this following services :

```
docker service create \
    --name whoami0 \
    --label traefik.port=80 \
    --network traefik-net \
    emilevauge/whoami
```

and check if your dashboard look like this :

![Imgur](https://i.imgur.com/LGOGEQB.png)


# License

![Apache 2.0 Licence](https://img.shields.io/hexpm/l/plug.svg)

This project is licensed under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license - see the [LICENSE](LICENSE) file for details.

# Author Information
This role was created in 15/10/2018 by [PG3](https://pg3.io)

