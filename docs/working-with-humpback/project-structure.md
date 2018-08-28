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
Needs definition

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

## mysql
This folder contains the MYSQL configuration file (my.cnf) for the MYSQL container.

## nginx
Contains the nginx server configuration for the nginx container.

## patches

## profiles
Humpback by default create it's own installation profile, that profile is stored in this folder and it's content is symbolic linked to the folder `web/profiles/custom`

## root
Needs definition

## settings
This folder contains all the settings files required and the services.yml file required by drupal also all this files are symbolic linked into the folder `web/sites/`.

## solr
Contains all the Solr server config for the Humpback Solr container.

## tests
The objective of this folder is to store all the custom behat test for this project.

## themes
This directory contains the Custom Drupal Themes for this project, also this folder is symbolic linked in: `web/themes/custom`.

## web
In this folder is builded the complete drupal site, this folder never have to be added to the git history, is just to build the drupal site.

## .ahoy.yml
Defines some custom ahoy commands to execute certain docker commands.

## .editorconfig
EditorConfig helps developers define and maintain consistent coding styles between different editors and IDEs see [http://editorconfig.org/](http://editorconfig.org/).

## .env
This file is very important, with this file we have the possibility to change certain settings of the Humpback containers environment like the the local site domain making use of the environment variable `VIRTUAL_HOST`.

## behat.yml
This file provides all the behat testing framework configuration for our environment.

## composer.json
This file is the one in charge to keep the information about the required modules and libraries and the version of those packages, including the drupal core, for more information follow this [link](https://getcomposer.org/doc/01-basic-usage.md#composer-json-project-setup).

## composer.lock

## composer.patches.json

## docker-compose.yml

## env.example

## gulpfile.js
Gulp configuration file for our project.

## LICENSE
The License file for our project.

## package-lock.json

## package.json

## pantheon.yml
This provides the possibility to set advanced configuration to your pantheon environments, for more information look at this link: [pantheon.yml usage](https://pantheon.io/docs/pantheon-yml/)

## README.md
The readme file for your project.

## traefik.toml
