# aroundBika

AngularJS interface and REST webservice in front of BikaLims



## Requirements

You need [docker-engine](https://docs.docker.com/engine/installation/) and [docker-compose](https://docs.docker.com/compose/install/)

## Docker images

Docker images are available at these registries:

AngularJS interface and REST webservice:
https://quay.io/repository/crs4/aroundbika

Plone server with Bika Lims plugin:
https://hub.docker.com/r/gmauro/bikaplone/

iCAT server using local postgresql:
https://hub.docker.com/r/gmauro/boxed-irods/

iCommands client:
https://hub.docker.com/r/gmauro/icommands/


## Quick start

Clone the repository: `git clone https://github.com/crs4/aroundbika`

Cd into the docker directory: `cd aroundbika`

Pull containers images fro the hub: `./dcomp.sh pull`

Do the first setup of iRODS: `./dcomp.sh run irods /irods_first_setup`

Configure iRODs account for a rodsuser (default username: iuser): `./dcomp.sh run irods /irods_config`

Bring up the containers: `./dcomp.sh up -d`

Point your browser to:
`http://localhost:8080` and install the Bika plugin

then point your browser to:
`http://localhost:8081` and login to AngularJS interface in front of BikaLims

### How to use  iRODS icommands 

Open a bash shell into the icommands container: `docker exec run -ti icommands /bin/bash`

Init the iRODS environment of the user: `iinit`

### Default values

#### Plone
user: admin
password: admin

#### iRODS
iRODS version: 4.1.8
iRODS service account: irods
iRODS zone: tempZone
iRODS port: 1247
iRODS admin: rods
iRODS user: iuser
password: irods123

#### PostgresSQL
db host: localhost
db port: 5432
db name: ICAT
db user: irods
password: irods123



## Using this repository

Start by cloning the official repository:

`git clone https://github.com/crs4/aroundbika`

Since the repository makes use of submodules, you first need to initialize all the submodules:

`cd aroundbika`
`git submodule update --init`

Alternatively, with version 1.6.5 of git and later, you can pass the --recursive option to git clone and initialize all submodules:

`git clone --recursive https://github.com/crs4/aroundbika`

