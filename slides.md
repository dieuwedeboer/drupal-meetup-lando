## Lando
### the best local dev in the galaxy

Install: [github.com/lando/lando](//github.com/lando/lando)

Docs: [docs.devwithlando.io](//docs.devwithlando)
<br><small>*(Seriously, read the docs)*</small>

<small>by Dieuwe de Boer</small>
<br>
<small>Sparks Interactive</small>



## 60 Second Demo

![Lando jumps to hyperspace](https://media.giphy.com/media/2SRvACIOCEOys/giphy.gif)


## Prerequisites

* [Download and install Lando.](//github.com/lando/lando/releases)
* Windows: you need Hyper-V enabled.
* Windows and OSX: installer bundles with Docker.
* Linux: you need to install Docker.
``` fish
sudo apt install docker-ce
```
<small>(That one Arch user can go compile it manually from source. Easy as.)</small>


## Engage the Hyperdrive

Using nothing but Lando:

<small>(no git, php, composer, etc, on the system)</small>

``` fish
mkdir demo && cd demo
lando init --recipe=drupal8 --webroot="drupal/web" --name="demo"
lando start
lando composer create-project sparksinteractive/sector-project drupal
```
<small>
* You'll likely run a *git clone* instead of *mkdir* and *composer*.
* If the project contains a *.lando.yml*, you just need to run *lando start*.
* The *lando init* command will also interactively prompt you for options.

</small>


## Let's visit the site

[http://demo.lndo.site:8000](http://demo.lndo.site:8000)

There is also HTTPS, and if you don't have a local Apache running you won't be assigned the port number.


## Enter DB credentials and install Drupal.

* For D8, creds default to "drupal7@drupal7:drupal7@database. [Check that format.]
* You can view any config you need by running *lando info*.
* You can quickly import and export with *lando db-import* and *lando db-export*.
* You can change the defaults and also configure as many DBs as you need.


## Done

![Yeah!](https://media.giphy.com/media/93qGSbfayiid2/giphy.gif)

How's that for developer onboarding?



## Demo with an existing project

* We've got Lando installed already.
* Git checkout the project.
* Drush sql-dump.
* Lando db-import
* [or from platform?]



## How it Works

* Uses Docker, but makes the containers talk to each other nicely.


## One config file to rule them all

* .lando.yml
* Can load in a docker-composer.yml
* Can load in my.cnf, php.ini, etc.
* Where things are located ~/.lando and stuff, location of DB on disk.
* Custom URls, php.ini, my.cnf, use apache or nginx, php versions


## *.lndo.site

* URL that they own, but DNS set to 127.0.0.1
* Add it to your /etc/hosts if you want to be 100% offline.
* There are always localhost ports for all services.
* You can route through any custom URL in your /etc/hosts or intranet DNS mask.


## Recipes

* Supports Drupal7 and Drupal8, also supports Pantheon specifically.


## Services

* Services, multiple DBs and mailhog.


## Config


## Tooling


## Debugging

* rebuilding, docker prune
* xDebug in action
* lando logs


## Custom Recipes and Commands?

* Pantheon special. You can do this yourself.


## Notes

* I find it much easier to still have a local and global copies of PHP, Composer, Drush, and other tools (e.g. Platform CLI, Pantheon CLI.)
* NGINX gateway 504s?
* Disk space... make Docker put all the things in custom directories?



## Questions?

![See ya](https://theplaylist.net/wp-content/uploads/2017/12/Lando-Calrissian-Jedi-Billy-Dee-Williams-1200x520.jpg)
