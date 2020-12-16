# KittMedia GitHub Workflow templates

Different workflow templates for different workflows.

## WoltLab

### build-application.yaml

Build a package and a fully installable application for WoltLab Suite.

### build-package.yaml

Build a package for WoltLab Suite.

### release-package.yaml

Creates a release when a tag is added and attach a built package to it.

## WordPress

### asset-compilation-and-minification.yml

Compiles SCSS/SASS and minifies CSS/JavaScript.

It assumes this structure:

```
|-- assets
|   |-- js
|   |   |-- some-js-file.js
|   `-- style
|       `-- scss
|           `-- style.scss
```

If you have a different structure, change the paths accordingly for the steps `Compile CSS` and `Minify JavaScript`.

Also runs `npm run build` and build an artifact with exclusions (requires a file in `.github/exclude_list`). Can be used for Gutenberg blocks via `@wordpress/scripts`.

#### Usage for a theme

For a theme, use a different destination for SCSS/SASS compilation as the files need to be in the root directory. The destination is already in the template but commented out. Comment out the earlier destination and remove the `#` sign of the theme destination (`destination: ${{ github.repository }}`).

### npm.yml

Runs `npm run build` and build an artifact with exclusions (requires a file in `.github/exclude_list`). Can be used for simple Gutenberg blocks via `@wordpress/scripts`.

## License

Our GitHub Action workflows are available for use and remix under the MIT license.
