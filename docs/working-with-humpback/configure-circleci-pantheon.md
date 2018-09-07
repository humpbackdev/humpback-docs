# Configure circleCI + Pantheon.

Humpback includes a basic template configuration to integrate CircleCI with your Drupal project, but as a template it needs your own information and configuration to make it work with your CircleCI account, that's why we are going to explain the basics steps to integrate your CircleCI account with our Drupal project.

The deploy steps of this integration works only with the Pantheon environment, but if you have your site hosted in another platform feel free to make all the required modifications over the deploy steps.

##.circleci folder structure

As you can see in the root path there is a folder named `.circleci`, this folder contains all the required configuration files your project.

####config.yml
This file contains all the required configuration to define each of the continuous steps (required docker images, bash scripts and so on.)

####{project name}
Contains the virtual host configuration for the circle ci environment.

#### {project name}.aliases.drushrc.php
This file provides the required drush aliases to use drush in the right way during the site building step.

#### settings.secret.php
Contains the drupal database credentials and any other settings required to make the site work correctly in the CircleCI environment.

##Defined workflow.
We already defined a basic CI workflow to deploy our Drupal site into the Pantheon environment, the following steps are the ones that we already define and partially configure with that objective.

####build
This step will be executed after each `git push` that you make to any branch and it's objective is to build the complete site, importing configuration, executing behat tests, testing coding standards and so on.

####deploy
This step will be executed on push to the  master branch, also this step require that "build" steps was executed successfully. The main objective of this step is to deploy our code in the github master branch to our Pantheon master branch and import all the required configuration for the pantheon environment.

####deploy-test
It will move the new code from the `dev` to the `test` environment also it will execute all the required drush commands to import the configuration, execute updates and so on.

####deploy-live-hold
As it's name said, this step only to require a confirmation to deploy the latest code to the live environment.

####deploy-live
It moves all the new code in the `test` environment to the `live` environment and it apply all the new configuration and updates into the Pantheon live environment.

##Let's configure our CircleCI.yml

As you can see in this file there are already defined and partially configured CI steps that together makes a basic CI workflow.


- **Create a new ssh key:** using your computer create a new ssh key executing the following command:
```bash
$ ssh-keygen -t rsa -b 4096
```
- **Save your new ssh private key on CircleCI:**  Into your CircleCi Account there is a section called `SSH Permissions`, there you should add the new private key that you recently generate.

- **Copy the generated fingerprint:** Once you save your private key on the circleCI environment you should be able to see in the `SSH Permissions` section the fingerprint of your private key, copy that fingerprint and paste it into the `.circleci/config.yml`, specifically in the section:
```yml
- add_ssh_keys:
    fingerprints:
      # @TODO: Add ssh_key fingerprint here.
      - ""
```

- **Save your new public ssh key on Pantheon:**  Logged in into your Pantheon account, go your account settings and find the **SSH keys** section, there you should add the new public that you recently generated.

- **Generate a new pantheon machine token:**  Logged in into your Pantheon account, go your account settings and find the **Machine tokens** section, generate a new one, save it we will use it in the next step.

- **Create the PANTHEON_TOKEN environment variable in CircleCI:** Logged in into your CircleCI account find your project, find into the settings the environment variables section and a new one create a new using as a name `PANTHEON_TOKEN` and assign it the value of the **Pantheon Machine token** that you recently generated.

- **Create the SITE_UUID environment variable in CircleCI:** Logged in into your CircleCI account find your project, find into the settings the environment variables section and a new one create a new using as a name `SITE_UUID` and assign it as value the uuid of your site, this uuid is usually placed into the file `config/sync/system.site.yml`.

- **Configure the git credentials into the config.yml:** Now again into the file `.circleci/config.yml` we should add the git user email and the git user name that match with the one that we use to generated the machine token and place the public key. This configuration is placed into the deploy step, and looks like this:
```yml
name: Deploy
command: |
  # @TODO: Configure git.
  git config --global user.email ""
  git config --global user.name ""
  echo 'Host *' >> /root/.ssh/config
  echo '   StrictHostKeyChecking no' >> /root/.ssh/config
  ahoy site deploy master "Auto deploy triggered from master branch"
```

- **Test your new CI configuration:** Commit the `config.yml` changes and push it to your repository, it should trigger the build step on CircleCI.
