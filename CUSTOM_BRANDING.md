# Custom Antwerp Branding Core Guide
If you need a slightly different version of the Antwerp Branding Core for your project, you can easily create a custom version of it. Please take a moment and read through the following guidelines to get you started.

##  Fork the Antwerp Branding Core
The first step is to fork your own copy of the Antwerp Branding Core.
You can find a Fork button in the right upper corner of the [Antwerp Branding Core GitHub Page](https://github.com/a-ui/core_branding_scss) just for that.
For more information about forking a repository, you can check the [GitHub documentation](https://help.github.com/articles/fork-a-repo).

Don’t forget to update the repository name of your forked version so there can be no confusion on which repository you’re working on.
As a naming convention we suggest to use an all lowercase snake case, like `customname_branding_scss`.

##  Update files
###  Update files in the styles folder
####  main.scss
You start by updating the `main.scss` file with the files that you want to customize.

```
@import 'quarks';
```

Typically you will import a custom version of `_quarks.scss` but if you want to do other modifications like changing the font or let's say a button then you will need to modify files like `_base.scss` or `_atoms.scss`.
Have a look at other custom versions of the Branding Core like the [ACPaaS Branding](https://github.com/a-ui/acpaas_branding_scss) for some inspiration.

####  _quarks.scss
The quarks contain variables for colors, spacing, etc.
If you want to override some variables, you just import your custom version of the `quarks.variables`.

```
@import 'quarks/quarks.variables';
```

###  Remove unnecessary files from `styles` folder
Be sure that the `styles` folder only contains scss files that you have updated.
So don’t forget to remove the original scss files that you don’t update.

###  Update package.json
Update `package.json` with the project name, version number and url of your repository.
Also don’t forget to add the original Antwerp Branding Core package as a devDepency.
```
"devDependencies": {
  "@a-ui/core": "^3.0.3"
}
```

###  Update CHANGELOG.md
Replace the original `CHANGELOG.md` file with an updated version.
The format should be based on [Keep a Changelog](http://keepachangelog.com/) and follow [Semantic Versioning](https://semver.org/) guidelines for the versioning of your project.
###  Update README.md
Update the original `README.md` file with your project specific information.


##  Building
To build the project, run the following command in your command line:
```
gulp build
```

##  Publishing
###  Publish on npm

Build the documentation for your project and commit the updated documentation.
```
gulp docs
git add . && git commit -m "Updated docs"
```

Create the version number for your project and be sure to use [SemVer](http://semver.org/) for versioning. So choose a patch, a minor or a major version.
Push the update files and tags.
```
npm version patch|minor|major
git push && git push --tags
```

Publish your project on npm
To publish on npm, you must be a user on the npm registry.
```
npm publish
```

###  Publish on CDN

To be defined when Travis is implemented.