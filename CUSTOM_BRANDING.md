# Custom Antwerp Branding Core Guide
A quick guide on how to make a custom color scheme based on the Antwerp Branding Core.

## Fork the Antwerp Branding Core
* Fork your own copy of the [Antwerp Branding Core](https://github.com/a-ui/core_branding_scss).
* Check out the [GitHub documentation](https://help.github.com/articles/fork-a-repo) for more information about forking a repository.

Don’t forget to update the repository name of your forked version so there can be no confusion on which repository you’re working on.
As a naming convention we suggest to use an all lowercase snake case, like `customname_branding_scss`.

## Update files
### package.json
* Update `package.json` with the project name, version number and url of your repository.
* Add the original Antwerp Branding Core package as a devDepency.

```
"devDependencies": {
  "@a-ui/core": "^3.0.3"
}
```

### main.scss
* Start the `main.scss` file from scratch
* Import the none changed atomic parts from the Branding Core and add your customized quarks file.

```
@import 'quarks';
@import '@a-ui/core/dist/assets/styles/base';
@import '@a-ui/core/dist/assets/styles/utilities';
@import '@a-ui/core/dist/assets/styles/atoms';
@import '@a-ui/core/dist/assets/styles/molecules';
@import '@a-ui/core/dist/assets/styles/organisms';

@import '@a-ui/core/dist/assets/styles/aui';
```

### _quarks.scss
The quarks contain variables for colors, spacing, etc.

* Import your custom version of the `quarks.variables` to override the variables.

```
@import '@a-ui/core/dist/assets/styles/quarks/quarks.mixins';
@import '@a-ui/core/dist/assets/styles/quarks/quarks.functions';
@import '@a-ui/core/dist/assets/styles/quarks/quarks.colors';

@import 'quarks/quarks.variables';

@import '@a-ui/core/dist/assets/styles/quarks/quarks.variables';
```

### CHANGELOG.md
* Replace the original `CHANGELOG.md` file with an updated version.

The format should be based on [Keep a Changelog](http://keepachangelog.com/) and follow [Semantic Versioning](https://semver.org/) guidelines for the versioning of your project.

### README.md
* Update the original `README.md` file with your project specific information.

### Remove unnecessary files
* Remove the none updated scss files from the `styles` folder.

## Building
* Build the project with the `gulp build` command.
* Build the documentation with the `gulp docs` command.

## Extra steps
* Follow the [npm instructions](https://docs.npmjs.com/cli/publish) to publish the package on npm.

Typically you will import a custom version of `_quarks.scss` but if you want to do other modifications like changing the font or let's say a button then you will need to modify files like `_base.scss` or `_atoms.scss` as well.

Have a look at other custom versions of the Branding Core like the [ACPaaS Branding](https://github.com/a-ui/acpaas_branding_scss) for some inspiration.
