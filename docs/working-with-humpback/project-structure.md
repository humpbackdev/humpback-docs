# Project structure

When you generate your project with Humpback Generator, you'll get the following folders and files in the root path of your project.

## .ahoy
It contains the definition of custom ahoy commands for your site.

## .circleci
Contains a basic template to integrate your project with CircleCI.

## composer-scripts
Contains custom composer scripts for your project, like the one in charge of the drupal settings placing.

## config
In this folder all the drupal configuration files are stored.

## docs
It stores all the custom documentation of your project.

## drush
This directory contains commands, configuration and site aliases for Drush. See this [web page](https://packagist.org/search/?type=drupal-drush) for a directory of Drush commands installable via Composer.

## files
This folder contains all the files uploaded to your Drupal site. The folder `web/sites/default/files` is a symbolic link to this folder.

## gulp-task
This folder contains all the custom gulp task defined for the project. You could develop your own gulp tasks and put it in this folder to make it available to your project.

## modules
Contains all the custom modules developed in your custom project. Notice that `web/modules/custom` is a symbolic link to the folder `custom` that's is inside of this directory.

## mysql
This folder contains the MYSQL configuration file (my.cnf) for the MYSQL container.

## nginx
Contains the nginx server configuration for the nginx container.

## patches
This folder is exclusive to save the local patches for modules, libraries and so on.

## profiles
By default, Humpback Generator creates an installation profile for each project it generates, that profile is stored in this folder and its content is linked to the folder `web/profiles/custom` (by using a symbolic link).

## root
This folder is created so you can add files that you need to be placed in the root path of your project, for example the `.htaccess` file. All the files here will be symbolic linked into the `web` folder.

## settings
This folder contains all the settings files and the services.yml file required by drupal. All of this files are symbolic linked into the folder `web/sites/`.

## solr
Contains the Solr server config for the Humpback Solr container.

## tests
The purpose of this folder is to store all the custom behat test for the generated project.

## themes
This directory contains the Custom Drupal Themes for the project, also it is symbolic linked into: `web/themes/custom`.

## web
This folder is where the complete drupal site is built, it shouldn't be added to the git history, its goal is to store the artifact for local development.

## .ahoy.yml
Defines some ahoy commands.

## .editorconfig
EditorConfig helps developers define and maintain consistent coding styles between different editors and IDEs, see [http://editorconfig.org/](http://editorconfig.org/).

## .env
This file is very important, it allows us to change certain settings of the Humpback containers environment, for example using the environment variable `VIRTUAL_HOST`, we can change the local site domain.

## behat.yml
This file provides all the behat testing framework configuration for the environment.

## composer.json
This file is the one in charge to keep the information about the required modules and libraries and the version of those packages, including the drupal core. For more information follow this [link](https://getcomposer.org/doc/01-basic-usage.md#composer-json-project-setup).

## composer.lock

## composer.patches.json

## docker-compose.yml
It contains the Docker compose configuration for the current project containers. For more information about how it works, you can take a look  [here](https://docs.docker.com/compose/compose-file/).

## env.example
Example file for the .env file.

## gulpfile.js
Gulp configuration file for the project.

## LICENSE
The License file for the project.

## package-lock.json

## package.json

## pantheon.yml
This file provides the possibility to set advanced configuration to your pantheon environments. For more information look at: [pantheon.yml usage](https://pantheon.io/docs/pantheon-yml/)

## README.md
The readme file for your project.

## traefik.toml
It contains the configuration to be placed in the traefik container to configure the traefik app. For more information about this file, check this [link](https://docs.traefik.io/v1.0/toml/)
