## Lando
### the best local dev in the galaxy

Install: [github.com/lando/lando](https://github.com/lando/lando)

Docs: [docs.devwithlando.io](https://docs.devwithlando.io)
<br><small>*(Seriously, read the docs)*</small>

<small>by Dieuwe de Boer</small>
<br>
<small>Sparks Interactive</small>



## What is Lando?

![Check it out](https://uproxx.files.wordpress.com/2016/08/lando-han-solo.jpg)


>Lando is for developers who want to quickly specify and painlessly
>spin up the services and tools needed to develop their projects.
>It's a free, open source, cross-platform, local development
>environment and DevOps tool built on Docker container technology ...


## Features

* Easily mimic your production environment locally.
* Standardize your teams dev environments and tooling on OSX, Windows and Linux.
* Integrate with hosting providers like Pantheon.
* Store all of the above in a version controlled config file called *.lando.yml*.
* Easily customize or extend tooling, deployment options and basically
  any other functionality.
* Free yourself from the tyranny of inferior local development products.



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

[http://demo.lndo.site:8080](http://demo.lndo.site:8080)

* You can access via localhost.
* There are also untrusted HTTPS links generated.
* Lando will run from port 80 if it can.
* We'll talk about *<>.lndo.site* and custom URLs later.


## Install Drupal

* A default DB server (*database*) is created, with a database (*drupal8*)
  that you can access as user *drupal8* with password *drupal8*.
* You can view all config with *lando info*.
* You can quickly import and export the DB with *lando db-import* and *lando db-export*.
* You can change the defaults and also configure as many DBs as you need.


## Done

![Yeah!](https://media.giphy.com/media/93qGSbfayiid2/giphy.gif)

How's that for developer onboarding?



## Demo with an existing project

<small>(assuming host machine has git and global drush with aliases)</small>

``` fish
git clone hvtbq2bsensg6@git.au.platform.sh:hvtbq2bsensg6.git sector.org.nz
cd sector.org.nz
lando init
lando start
drush @sector-org-nz.master sql-dump > sector.sql
lando db-import sector.sql
```

<small>(you cannot import files outside of the lando root)</small>



## How it Works

* Lando is a wrapper for Docker that handles all the hard stuff like
  networking and making containers talk to each other.
* The docs are very good, let's [read the
  basics](https://docs.devwithlando.io/started.html).


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
* There is a "share" command. It's slow.


## Recipes

* Lando supports a very large set of languages and frameworks.
* D6, D7, D8.
* Demo *lando init pantheon*.

## Services

* Switch between *apache* and *nginx* with a single line change.
* Demo mailhog.
* Demo multiple DBs.


## Config

* Demo custom *php.ini* and custom *my.cnf*.


## Tooling

* Show platform tool and also the official example.


## Debugging

* lando logs
* lando rebuild
* docker system prune
* xDebug in action


## Issues and Thoughts

* I find it much easier to still have a local and global copies of
  PHP, Composer, Drush, and other tools (e.g. Platform CLI, Pantheon
  CLI.)
* NGINX gateway 504s?
* Disk space... make Docker put all the things in custom directories?
* Drush aliases.
* Modify anything in the containers manually and that will be lost on
  rebuild, but your filesystem and database will continue to persist.



## Questions?

![See ya](https://theplaylist.net/wp-content/uploads/2017/12/Lando-Calrissian-Jedi-Billy-Dee-Williams-1200x520.jpg)


![It's a wrap](https://i.imgflip.com/28itn8.jpg)
