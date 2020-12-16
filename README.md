# KittMedia GitHub Workflow templates

Different workflow templates for different workflows.

## WoltLab

### build-application.yml

Build a package and a fully installable application for WoltLab Suite.

### build-package.yml

Build a package for WoltLab Suite.

### release-package.yml

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

## miscellaneous

### ssh-upload-steps.yml

To upload data via SSH, you can use these steps to do so (if you need to do something before, e.g. compiling, do that before). It will use a command using `ssh` as well as one with `scp`.

The file(s) will then be uploaded to the remote host specified in the directory `<remote path>/repo-name/sha-hash/repo-name.tar.gz`. You can change these paths by modifying the two parts `${{ secrets.REMOTE_PATH_BASE }}/${{ github.event.repository.name }}/${{ github.sha }}`.

If the directory does not exist, it will be created first.

If you want to upload only specific files, change the `*` at the `scp` command to your desired file list.

#### Variables

You need some variables as secrets to get the upload working.

##### KNOWN_HOSTS

Get a known host via `ssh-keyscan example.com`.

##### REMOTE_PATH_BASE

The path where the package should be uploaded.

##### REMOTE_HOST

Set your remote host, e. g. `example.com`.

##### REMOTE_USER

Set your remote user, e.g. `root` (please, do not!).

##### SSH_PRIVATE_KEY

Generate a private key with `ssh-keygen -m PEM -t rsa -b 4096`.

Make sure the public key is set on the target server in the `known_hosts` file of SSH.

## License

Our GitHub Action workflows are available for use and remix under the MIT license.
