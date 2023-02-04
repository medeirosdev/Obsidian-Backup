# An introduction to the NPM package manager
`npm` is the standard package manager for Node.js.

In September 2022 over 2.1 million packages were reported being listed in the npm registry, making it the biggest single language code repository on Earth, and you can be sure there is a package for (almost!) everything.

It started as a way to download and manage dependencies of Node.js packages, but it has since become a tool used also in frontend JavaScript.

[**Yarn**](https://yarnpkg.com/en/) and [**pnpm**](https://pnpm.io/) are alternatives to npm cli. You can check them out as well.

## [](https://nodejs.dev/en/learn/an-introduction-to-the-npm-package-manager/#packages)Packages

`npm` manages downloads of dependencies of your project.

### [](https://nodejs.dev/en/learn/an-introduction-to-the-npm-package-manager/#installing-all-dependencies)Installing all dependencies

If a project has a `package.json` file, by running

BASHcopy

npm install

it will install everything the project needs, in the `node_modules` folder, creating it if it's not existing already.

### [](https://nodejs.dev/en/learn/an-introduction-to-the-npm-package-manager/#installing-a-single-package)Installing a single package

You can also install a specific package by running

BASHcopy

npm install <package-name>

Furthermore, since npm 5, this command adds `<package-name>` to the `package.json` file _dependencies_. Before version 5, you needed to add the flag `--save`.

Often you'll see more flags added to this command:

-   `--save-dev` installs and adds the entry to the `package.json` file _devDependencies_
-   `--no-save` installs but does not add the entry to the `package.json` file _dependencies_
-   `--save-optional` installs and adds the entry to the `package.json` file _optionalDependencies_
-   `--no-optional` will prevent optional dependencies from being installed

Shorthands of the flags can also be used:

-   -S: `--save`
-   -D: `--save-dev`
-   -O: `--save-optional`

The difference between _devDependencies_ and _dependencies_ is that the former contains development tools, like a testing library, while the latter is bundled with the app in production.

As for the _optionalDependencies_ the difference is that build failure of the dependency will not cause installation to fail. But it is your program's responsibility to handle the lack of the dependency. Read more about [optional dependencies](https://docs.npmjs.com/cli/v7/configuring-npm/package-json#optionaldependencies).

### [](https://nodejs.dev/en/learn/an-introduction-to-the-npm-package-manager/#updating-packages)Updating packages

Updating is also made easy, by running

BASHcopy

npm update

`npm` will check all packages for a newer version that satisfies your versioning constraints.

You can specify a single package to update as well:

BASHcopy

npm update <package-name>

## [](https://nodejs.dev/en/learn/an-introduction-to-the-npm-package-manager/#versioning)Versioning

In addition to plain downloads, `npm` also manages **versioning**, so you can specify any specific version of a package, or require a version higher or lower than what you need.

Many times you'll find that a library is only compatible with a major release of another library.

Or a bug in the latest release of a lib, still unfixed, is causing an issue.

Specifying an explicit version of a library also helps to keep everyone on the same exact version of a package, so that the whole team runs the same version until the `package.json` file is updated.

In all those cases, versioning helps a lot, and `npm` follows the semantic versioning (semver) standard.

You can install a specific version of a package, by running

BASHcopy

npm install <package-name>@<version>

## [](https://nodejs.dev/en/learn/an-introduction-to-the-npm-package-manager/#running-tasks)Running Tasks

The package.json file supports a format for specifying command line tasks that can be run by using

BASHcopy

npm run <task-name>

For example:

JSONcopy

{
  "scripts": {
    "start-dev": "node lib/server-development",
    "start": "node lib/server-production"
  }
}

It's very common to use this feature to run Webpack:

JSONcopy

{
  "scripts": {
    "watch": "webpack --watch --progress --colors --config webpack.conf.js",
    "dev": "webpack --progress --colors --config webpack.conf.js",
    "prod": "NODE_ENV=production webpack -p --config webpack.conf.js"
  }
}

So instead of typing those long commands, which are easy to forget or mistype, you can run

BASHcopy

$ npm run watch
$ npm run dev
$ npm run prod