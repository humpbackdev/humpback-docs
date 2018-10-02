# Using your local version of the Humpback generator.

- Clone the `generator-humpback` (https://github.com/humpbackdev/generator-humpback) repository in to your local environment.
- Do all the changes that you need over the Humpback generator.
- Located over the `generator-humpback` root path execute:
```bash
npm install
```
- Over same path execute the following command to link your local generator version with npm global package registry:
```bash
npm link
```
-  Now you are able to use your local version of the `generator-humpback`, to use it just execute following `yo` command:
```bash
yo humpback
```
It should build a new project with new changes that you recently introduce to the generator.  

If you want to remove the link to your local version of the `generator-humpback`  just execute the following command into the `generator-humpback` root path:
```bash
npm unlink
```
