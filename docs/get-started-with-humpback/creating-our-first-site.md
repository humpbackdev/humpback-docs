
# Creating our first project.


## Generating a site
First at all, create your new project folder and get into it:

```bash
mkdir my-project && cd my-project
```

Generate your new project files and execute the following Yeoman command and follow the instructions given by the generator.

```bash
yo humpback
```

### Generate the Drupal settings file.

Our next step is pretty easy, we need to generate the Drupal settings files, for this propose Humpback provides a custom command to generate them and placed them in the right place, the command is:

```bash
ahoy site local-settings
```

### Prepare your local site.

Now we need to download the contrib modules, patches, Drupal core and other required libraries to execute our site and work with it.

First execute:
```bash
ahoy composer install
```
Then execute:
```bash
npm install
```

### Turn on your new beast

First we need to "Turn on" all the docker containers that will provide us all awesome features that humpback have.
If this is the first time that you execute this command for your project it probably will take some time, because it needs to download all the docker images and configure them.

```bash
ahoy up
```

### Install the Drupal site.

Now we need to install the Drupal in our environment. To install it Humpback provides a custom command, this command could be execute as many times as is required.
This command is responsible of:

- Wipe existing data base tables.
- Execute the Drupal installation process.
- Import all the existing configuration.

To do this just execute:
```bash
ahoy site install
```
This command will use the default included installation profile to install your site; if you need to change the profile, see [Using different installation profile](../working-with-humpback/using-different-installation-profile.md)

### Get your brand new site url

Humpback provides beautiful urls for the sites that are generated with it, to get your site url execute:

``` bash
ahoy docker url
```

And that's it!! Now you have totally functional Drupal site working with humpback.
