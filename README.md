# aroundBika

 Multi-container Docker application for the CRS4 
 infrastructure to support NGS laboratory automation.
 
 Containers included:  
* AngularJS web interface - [bika.penelope](https://github.com/ratzeni/bika.penelope)
* REST webservice - [bika.webservice](https://github.com/ratzeni/bika.webservice)
* RabbitMQ
* Flower 

All activities on the CRS4 wet-lab are tracked using BIKA-LIMS, an open 
source, community based LIMS.  
A custom web interface, based on an AngularJS and a REST web-service, 
has been created to expose the LIMS to the wet-lab technicians.  
RabbitMQ and Flower are parts of a messages-driven automation system 
to handle sequencing data produced from the CRS4 large scale NGS Core 
facility (see [PRESTA](https://github.com/gmauro/presta)).

## Requirements

You need [docker-engine](https://docs.docker.com/engine/installation/) 
and [docker-compose](https://docs.docker.com/compose/install/)  
See [docker-compose docs](https://docs.docker.com/compose/reference/overview/)


## Docker images

Docker images are available at these registries:  
REST webservice:
https://quay.io/repository/crs4/bika.webservice

Any commit in this repository will engage a build trigger on [Quay.io](https://quay.io)

## Quick start

Clone the repository:  
```bash
git clone -- recursive https://github.com/crs4/aroundbika
```

Cd into the docker directory:  
```bash
cd aroundbika
```

Pull containers images fro the hub:  
```bash
./dcomp.sh pull
```

Create and edit bika.penelope configuration:  
```bash
cp bika.penelope/app/init.module.js.sample bika.penelope/app/init.module.js 
nano bika.penelope/app/init.module.js
```

Bring up the containers:  
```bash
./dcomp.sh up -d
```

Point your browser to:  
`http://localhost:80` 
and login to AngularJS interface using Bika credentials
