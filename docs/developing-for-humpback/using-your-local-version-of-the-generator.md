# Using your local version of the Humpback Generator

- Clone the [`generator-humpback`](https://github.com/humpbackdev/generator-humpback) repository directly or fork the project and then clone it into your local environment.
- Located over the `generator-humpback` root path execute:
```bash
npm install
```
- Do all the changes that you need over the Humpback Generator.
- On same path, execute the following command to link your local generator version with npm global package registry:
```bash
npm link
```
-  Now, you are able to use your local version of the `generator-humpback`, to use it just execute following `yo` command:
```bash
yo humpback
```
It should build a new project with the changes that you introduced to the generator.

If you want to remove the link to your local version of the `generator-humpback`, you just need to execute the following command into the `generator-humpback` root path:
```bash
npm unlink
```

## Important!!!

If you think that your changes to the Humpback generator would help other people or improve any existing process: PLEASE send a pull request with your changes.
