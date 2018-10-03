# Using your local version of the Humpback generator.

- Clone the `generator-humpback` (https://github.com/humpbackdev/generator-humpback) repository directly or fork the project and then clone it in to your local environment.
- Located over the `generator-humpback` root path execute:
```bash
npm install
```
- Do all the changes that you need over the Humpback generator.
- Over same path execute the following command to link your local generator version with npm global package registry:
```bash
npm link
```
-  Now you are able to use your local version of the `generator-humpback`, to use it just execute following `yo` command:
```bash
yo humpback
```
It should build a new project with the new changes that you recently introduced to the generator.

If you want to remove the link to your local version of the `generator-humpback`  just execute the following command into the `generator-humpback` root path:
```bash
npm unlink
```

## Very important note:

If you think that your changes to the Humpback generator could help to other people or they improve some existing process feel free to send us a pull request with your changes.
