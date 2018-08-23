
# Generating our first project.


## Generating a site
First at all create your new project folder and get into it:

```bash
mkdir my-project && cd my-project
```

Generate your new project files execute the following Yeoman command and following the instructions given by the generator.

```bash
yo humpback
```

### Prepare your local site.

Now we need to download the contrib modules, patches and the Drupal 8 core and other libraries required by to execute our site and work with it.

First execute:
```bash
composer install
```
Then execute:
```bash
npm install
```

### Generate the Drupal settings file.

Our next step is pretty easy, we need to generate the Drupal settings files, for this propose Humpback provides a custom command to generate them and placed in the right place, the command is:

```bash
ahoy site local-settings
```

### Turn on your new beast

First we need to "wake  up" all the our docker containers that will provide us all awesome features that humpback have. If is the first time that you execute this command for your project it probably will take some time because it needs to download all the docker images and configure them to our environment work in the right way.

```bash
ahoy up
```

### Install the Drupal site.

Now we need to install the Drupal 8 in our environment, to install it Humpback provides a custom command, this command could be execute as many times as is required.
This command will be the responsible of:

- Wipe existing data base tables.
- Execute the Drupal installation process.
- Import all the existing configuration.

To do this just execute:
```bash
ahoy site install
```

### Get your brand new site url

Humpback provides beautiful urls for the sites that are generated with it, to get your site url execute:

``` bash
ahoy docker url
```

And that's it!! Now you a totally functional Drupal 8 site working with humpback.