
# Creating our first project


## Generating a site
First of all, create your new project folder and get into it:

```bash
mkdir my-project && cd my-project
```

Generate your new project files by executing the following Yeoman command and following the instructions given by the generator.

```bash
yo humpback
```

### Generate the Drupal settings file

Our next step is pretty easy, we need to generate the Drupal settings files, Humpback provides a command to generate them in the right place, the command is:

```bash
ahoy site local-settings
```

### Prepare your local site

Now we need to download the contrib modules, patches, Drupal core and other required libraries to execute our site and work with it. In order to do so you'll have to run:

```bash
ahoy composer install

npm install
```

### Turn on your new beast

First we need to "turn on" all the docker containers that will provide us all the awesome features that Humpback has.
If it is the first time that you execute this command for your project, it will probably take some time, because it needs to download all the docker images and configure them. You'll have to run the command:

```bash
ahoy up
```

### Install the Drupal site

Now we need to install Drupal in our environment. To install it, Humpback provides a command, this command can be executed as many times as needed. It is responsible of:

- Wipe existing data base tables.
- Run the Drupal installation process.
- Import all the existing configuration.

To do this, you just need to execute:

```bash
ahoy site install
```

This command will install Drupal using the default installation profile; but if you need to use other profile you can go and see [Using different installation profile](../working-with-humpback/using-different-installation-profile.md)

### Get your brand new site URL

Humpback provides beautiful URLs for the sites that are generated with it, to get your site URL execute:

``` bash
ahoy docker url
```

And that's it!! Now you have a totally functional Drupal site working with Humpback.
