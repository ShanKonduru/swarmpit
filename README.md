[![swarmpit](http://swarmpit.io/img/logo-swarmpit.svg?r1)](http://swarmpit.io)

Lightweight mobile-friendly Docker Swarm management UI

[![gitter](https://badges.gitter.im/trezor/community.svg)](https://gitter.im/swarmpit_io/swarmpit) [![Build Status](https://travis-ci.org/swarmpit/swarmpit.svg?branch=master)](https://travis-ci.org/swarmpit/swarmpit)

<img src="https://raw.githubusercontent.com/swarmpit/swarmpit/master/resources/public/imac.png">

Swarmpit provides simple and easy to use interface for your Docker Swarm cluster. You can manage your stacks, services, secrets, volumes, networks etc. After linking your Docker Hub account or custom registry, private repositories can be easily deployed on Swarm. Best of all, you can share this management console securely with your whole team.

More details about future and past releases can be found in [ROADMAP.md](ROADMAP.md)

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/fold_left.svg?style=social&label=Follow%20%40swarmpit_io)](https://twitter.com/swarmpit_io)

## Installation

The only dependency for Swarmpit deployment is Docker with Swarm initialized, we are supporting Docker 1.13 and newer.

### Package installer
Installer is your guide to setup swarmpit platform. For more details see installer [repo](https://github.com/swarmpit/installer)

#### Stable version
Deploy our current milestone version

```
docker run -it --rm \
  --name swarmpit-installer \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  swarmpit/install:1.6
```

#### Edge version
Deploy latest version for the brave and true

```
docker run -it --rm \
  --name swarmpit-installer \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  swarmpit/install:edge
```
### Manual installation
Simply deploy Swarmpit by using a compose file from our git repo.

```
git clone https://github.com/swarmpit/swarmpit
docker stack deploy -c swarmpit/docker-compose.yml swarmpit
```

[This stack](docker-compose.yml) is a composition of Swarmpit, its agent and CouchDB. Feel free to edit the stackfile to change an application port and we strongly recommend to specify `db-data` volume driver to shared-volume type of your choice. Alternatively, you can link db service to the specific node by using [constraint](https://docs.docker.com/compose/compose-file/#placement).

Swarmpit is published on port `888` by default.

## Development

Swarmpit is written purely in Clojure and utilizes React on front-end. CouchDB is used to store data, that cannot be stored directly in Docker API.

Everything about building, issue reporting and setting up development environment can be found in [CONTRIBUTING.md](CONTRIBUTING.md)

## Demo

[![Try in PWD](https://cdn.rawgit.com/play-with-docker/stacks/cff22438/assets/images/button.png)](http://play-with-docker.com?stack=https://raw.githubusercontent.com/swarmpit/swarmpit/master/docker-compose.yml) 

Deploys Swarmpit to play-with-docker sandbox. Please wait few moments till application is up and running before accessing
port 888. Initialization might take a few seconds.
