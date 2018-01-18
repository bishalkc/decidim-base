
[Decidim](https://decidim.org) is a participatory democracy framework, written in Ruby on Rails, originally developed for the Barcelona City government online and offline participation website. Installing these libraries will provide you a generator and gems to help you develop web applications like the ones found on [example applications](#example-applications) or like [our demo application](http://staging.decidim.codegram.com).



Setting up the development environment of [Decidim] (https://github.com/decidim/decidim) with Docker
### Overview

1. For Linux users, we need you to install [Docker engine](https://docs.docker.com/engine/installation/) and [Docker compose](https://docs.docker.com/compose/install/). Make sure you have Docker compose version 1.6 or higher by executing

```shell
$ docker-compose version
```

2. For PC and Mac users we need you to install [Docker toolbox for Mac and Windows](https://www.docker.com/products/docker-toolbox) and use [Docker Machine](https://docs.docker.com/machine/get-started/) to create a virtual machine to run your Docker containers. Once your machine is created and you have connected your shell to this new machine, you're ready to run Docker commands on this host. If you're using Linux you can skip to the next step.

### Prepare the code
```
$ git clone
$ cd decidim_base
$ mkdir -p pg-data redis-data
```

### run the app  
```
$ docker-compose up -d
$ docker-compose run decidim_app rake db:migrate db:seed
$ docker-compose restart
```

### Seeding the databases  

```shell
$ docker-compose run decidim_app run db:migrate db:seed
```

### Accessing the Docker host

If you are using Docker Machine, run this command to get your current Docker host's IP:

```shell
$ docker-machine ip <your_docker_machine_name>
```


#### Browse Decidim

After you create a development app (`bundle exec rake development_app`):

* `cd decidim_base`
* `docker-compose up -d`
* Go to 'https://localhost:3000'
   Note: You will have to accept the cert warning
Optionally, you can log in as: user@example.org | decidim123456

Also, if you want to verify yourself against the default authorization handler use a document number ended with "X".

#### Browse Admin Interface

After you create a development app (`bundle exec rake development_app`):

* `cd decidim_base`
* `docker-compose up -d`
* Go to 'https://localhost:3000/user/sign_in'
* Login data: admin@example.org | decidim123456
   Note: You will have to accept the cert warning

#### Browse System Admin Interface   
* Go to 'https://localhost:3000/admin'
* Login data: system@example.org | decidim123456
   Note: You will have to accept the cert warning

## Example applications

Since Decidim is a ruby gem, you can check out the [dependent repositories](https://github.com/decidim/decidim/network/dependents?type=application) to see how many applications are on the wild or tests that other developers have made. Here's a partial list with some of the projects that have used Decidim:

* [Demo](http://staging.decidim.codegram.com)
* [Decidim Barcelona](https://decidim.barcelona) - [View code](https://github.com/AjuntamentdeBarcelona/decidim-barcelona)
* [L'H ON Participa](https://www.lhon-participa.cat) - [View code](https://github.com/HospitaletDeLlobregat/decidim-hospitalet)
* [Decidim Terrassa](https://participa.terrassa.cat) - [View code](https://github.com/AjuntamentDeTerrassa/decidim-terrassa)
* [Decidim Sabadell](https://decidim.sabadell.cat) - [View code](https://github.com/AjuntamentDeSabadell/decidim-sabadell)
* [Decidim Gavà](https://participa.gavaciutat.cat) - [View code](https://github.com/AjuntamentDeGava/decidim-gava)
* [Decidim Sant Cugat](https://decidim.santcugat.cat/) - [View code](https://github.com/AjuntamentdeSantCugat/decidim-sant_cugat)
* [Vilanova Participa](http://participa.vilanova.cat) - [View code](https://github.com/vilanovailageltru/decidim-vilanova)
* [Erabaki Pamplona](https://erabaki.pamplona.es) - [View code](https://github.com/ErabakiPamplona/erabaki)
* [Decidim Mataró](https://www.decidimmataro.cat) - [View code](https://github.com/AjuntamentDeMataro/decidim-mataro)
* [Commission Nationale du Débat Public (France)](https://cndp.opensourcepolitics.eu/)
* [MetaDecidim](https://meta.decidim.barcelona/) - [View Code](https://github.com/decidim/metadecidim)