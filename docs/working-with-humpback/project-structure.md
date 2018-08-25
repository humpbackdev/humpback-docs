# Project structure

When the Humpback generator generates your project it give as result the following folders and files in the root path of your project

## .ahoy
it contains the definition of custom ahoy commands for your site.

## .circleci
Contains a basic template to integrate your project with circleCI

## composer-scripts
Contains custom composer scripts for your project, like the one in charge of the drupal settings placing.

## config
In this folder is stored all the drupal configuration files.

## content

## docs
The objective of this folder is to store all the custom documentation of your project.

## drush
This directory contains commands, configuration and site aliases for Drush. See this [web page](https://packagist.org/search/?type=drupal-drush) for a directory of Drush commands installable via Composer.

## files
This folder will contain all the files uploaded to your Drupal site. The folder `web/sites/default/files` is a symbolic link of this folder.

## gulp-task
This folder contains all our custom gulp task defined for the project. Also you could develop your own gulp task put it in this folder to make available to your project.

## modules
This folder will contain all the custom modules developed your custom project. The Folder  `web/modules/custom` is a symbolic link of the folder `custom` that's is inside of this folder.

- mysql
- nginx
- patches
- profiles
- root
- settings
- solr
- tests
- themes
- web
- .ahoy.yml
- .editorconfig
- .env
- behat.yml
- composer.json
- composer.lock
- composer.patches.json
- docker-compose.yml
- env.example
- gulpfile.js
- LICENSE
- package-lock.json
- package.json
- pantheon.yml
- README.md
- traefik.toml
