## Lando
### the best local dev in the galaxy

Install: [github.com/lando/lando](//github.com/lando/lando)

Docs: [docs.devwithlando.io](//docs.devwithlando)
<br><small>*(Seriously, read the docs)*</small>

<small>by Dieuwe de Boer</small>
<br>
<small>Sparks Interactive</small>



## Sixty Second Demo

[find appropriate gif]

[check this section, and run through it, a few times]


## Pre-requisites

* [Download and install Lando.](//github.com/lando/lando/releases)
* Windows: you need Hyper-V enabled.
* Windows and OSX: installer bundles with Docker.
* Linux: `sudo apt install docker-ce`.
<br><small>(That one Arch user can go compile it manually from source. Easy as.)</small>


## Nearly done!

``` fish
mkdir one-minute && cd one-minute
lando init --recipe=drupal8 --webroot="." --name="one-minute"
lando start
lando ssh -c "composer create-project sparksinteractive/sector-project ."
```

You'd likely run a git checkout instead of the `mkdir` and `composer` commands.

If the project contains a `.lando.yml`, you just need to run `lando start`.

The `lando init` command will also interactively prompt you for options.


## Let's visit the site

[http://drupal-meetup-demo.lndo.site:8000](http://drupal-meetup-demo.lndo.site:8000)

There is also HTTPS, and if you don't have a local Apache running you won't be assigned the port number.


## Enter DB credentials and wait for your site to install.

For D7, creds default to "drupal7@drupal7:drupal7/database. [Check that format LOL]

You can view any config you need by running `lando info`.

You can import a DB into the default database container with `lando db-import`. There is a matching export command and you can obviously also specify the database if you have more than one on a project.


## Done

How's that for developer onboarding?


## Let's do it again, but faster and with an existing project.

* We've got Lando installed already.
* Git checkout the project.
* Drush sql-dump.
* Lando db-import
* [or from platform?]



## How it Works

* Uses Docker, but makes the containers talk to each other nicely.


## .lando.yml - one config file to rule them all

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
