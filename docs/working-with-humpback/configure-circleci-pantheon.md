# Configure CircleCI + Pantheon

Humpback includes a basic template configuration to integrate CircleCI with your Drupal project but, as a template, it needs your own information and configuration to make it work with your CircleCI account, that's why we are going to explain the basics steps to integrate your CircleCI account with your Drupal project.

The deploy steps of this integration work only with the Pantheon environment, anyways, if you have your site hosted in another platform, feel free to make all the modifications you need over the deploy steps.

##.circleci folder structure

As you can see in the root path, there is a folder named `.circleci`, this folder contains all the required configuration files for your project.

####config.yml
This file contains all the required configuration to define each of the continuous steps (required docker images, bash scripts and so on.)

####{project name}
Contains the virtual host configuration for the CircleCI environment.

#### {project name}.aliases.drushrc.php
This file provides the required drush aliases to use drush in the right way during the site building step.

#### settings.secret.php
Contains the drupal database credentials and any other settings required to make the site work correctly in the CircleCI environment.

##Defined workflow
We already defined a basic CI workflow to deploy Drupal sites into the Pantheon environment, the following steps are the ones that we already defined and partially configured with that objective.

####build
This step will be executed after each `git push` that you make to any branch and its goal is to build the complete site, import configuration, execut behat tests, test coding standards and so on.

####deploy
This step will be executed on push to the master branch, also it requires that all the "build" steps were executed successfully. The main purpose of this step is to deploy the code in the github master branch to the Pantheon master branch and import all the required configuration for the Pantheon environment.

####deploy-test
It will move the new code from the `dev` to the `test` environment, it will also execute all the required drush commands to import the configuration, execute updates and so on.

####deploy-live-hold
As it is said in its name, this step is just for holding on the deploy to the live environment; basically, it requires a manual confirmation to deploy the latest code to the live environment.

####deploy-live
It moves all the new code in the `test` environment to the `live` environment and it apply all the new configuration and updates into the Pantheon live environment. In order to be run, it is needed that the user manually approved this step in the previous one (the `deploy-live-hold`).

##Let's configure the circleci.yml

In this file, there are already defined and partially configured CI some steps that together make a basic CI workflow.

- **Create a new SSH key:** using your computer, create a new ssh key by executing the following command:
```bash
$ ssh-keygen -t rsa -b 4096
```

- **Save your new SSH private key on CircleCI:**  in your CircleCi Account there is a section called `SSH Permissions`, there you should add the new private key that you recently generated.

- **Copy the generated fingerprint:** once you save your private key on the CircleCI environment, you should be able to see, in the `SSH Permissions` section, the fingerprint of your private key, you should copy that fingerprint and paste it into the `.circleci/config.yml` file, specifically in the section:
```yml
- add_ssh_keys:
    fingerprints:
      # @TODO: Add ssh_key fingerprint here.
      - ""
```

- **Save your new public SSH key on Pantheon:** log in into your Pantheon account, go to your account settings and find the **SSH keys** section, there you should add the new public key that you recently generated.

- **Generate a new pantheon machine token:**  while logged in into your Pantheon account, go to your account settings and find the **Machine tokens** section, generate a new one and save it, it will be used in the next step.

- **Create the PANTHEON_TOKEN environment variable in CircleCI:** log in into your CircleCI account, find your project, go to settings, find the environment variables section and create a new one using `PANTHEON_TOKEN` as the name and assign it the value of the **Pantheon Machine token** that you recently generated.

- **Create the SITE_UUID environment variable in CircleCI:** while logged in into your CircleCI account, find your project, go to settings, find the environment variables section and create a new one using `SITE_UUID` as the name and assign it as value the UUID of your site (this UUID is usually placed into the file `config/sync/system.site.yml`).

- **Configure the git credentials into the config.yml:** go again to the file `.circleci/config.yml`, in there you should add the git user email and the git user name that match with the one that you used to generate the machine token and place the public key. This configuration is placed into the deploy step, and looks like this:

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

- **Test your new CI configuration:** commit the `config.yml` changes and push it to your repository, it should trigger the build step on CircleCI.
