# TestNgUpdate

This repo is a experiment of a rolling update from v6.2.9 at the time of v18.2.4 following [the Angular update guide](https://angular.dev/update-guide) to see what errors I encounter.

# From v7.2.16 to v8
The CLI asks for the the current node LTS
```
$ NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@8 update @angular/cli@8 @angular/core@8

The installed Angular CLI version is older than the latest stable version.
Installing a temporary version to perform the update.
Installing packages for tooling via npm.
Installed packages for tooling via npm.
Node.js version v10.24.1 detected.
The Angular CLI requires a minimum Node.js version of v18.19.

Please update your Node.js version or visit https://nodejs.org/ for additional instructions.
```

# From v6.2.9 to v7.2.16
ran `NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@7 update @angular/cli@7 @angular/core@7`

> The update went smooth. No errors at all

# Meta

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.2.9.