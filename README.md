# TestNgUpdate

This repo is a experiment of a rolling update from v6.2.9 at the time of v18.2.4 following [the Angular update guide](https://angular.dev/update-guide) to see what errors I encounter.

#  From v11.2.14 to v12.2.18
ran `ng update @angular/core@12 @angular/cli@12`

> The update went smooth. No errors at all

# From v10.2.5 to v11.2.14
ran `ng update @angular/core@11 @angular/cli@11`

> The update went smooth. No errors at all

# From v9.1.13 to v10.2.5
```
$ npx @angular/cli@10 update @angular/core@10 @angular/cli@10

Your global Angular CLI version (10.2.4) is greater than your local version (9.1.15). The local Angular CLI version is used.

To disable this warning use "ng config -g cli.warnings.versionMismatch false".
The installed local Angular CLI version is older than the latest stable version.
Installing a temporary version to perform the update.
Installing packages for tooling via npm.
Installed packages for tooling via npm.
Node.js version v12.22.12 detected.
The Angular CLI requires a minimum Node.js version of v18.19.

Please update your Node.js version or visit https://nodejs.org/ for additional instructions.
```

> Running `$ NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@10 update @angular/core@10 @angular/cli@10` will not prompt to update your node to v18.  
You might get the following error:  
```
▸ Update 'module' and 'target' TypeScript compiler options.
  Read more about this here: https://v10.angular.io/guide/migration-update-module-and-target-compiler-options
    Unable to update 'tsconfig.json' module option from 'esnext' to 'es2020': Failed to parse "tsconfig.json" as JSON AST Object. PropertyNameExpected at location: 467.
    Unable to update 'e2e/tsconfig.json' target option from 'es5' to 'es2018': Could not read 'e2e/tsconfig.json'.
  Migration completed.

▸ Removing "Solution Style" TypeScript configuration file support.
✖ Migration failed: Failed to parse "tsconfig.json" as JSON AST Object. PropertyNameExpected at location: 467.
  See "/tmp/ng-i1taW1/angular-errors.log" for further details.
```

> The following migrations will fail `update-module-and-target-compiler-options`, `remove-solution-style-tsconfig`  
To make those migrations work, we have to remove trailing commas from the tsconfig.json  
To also fix the `update-module-and-target-compiler-options` migration, we have to rename e2e/tsconfig.e2e.json to tsconfig.json, run the migration, and then rename it back.  
We can make those changes before updating. But if updated and the migrations failed, we can rerun the migrations with: `NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@10 update @angular/cli@10 --migrate-only --from=9.1.13 --to=10.2.5`

# From v8.2.14 to v9.1.13
ran `NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@9 update @angular/core@9 @angular/cli@9`

> The update went smooth. No errors at all

# From v7.2.16 to v8.2.14
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

> After pinning node 10, and running the command again, the command ran OK and tried ran all migrations.

# From v6.2.9 to v7.2.16
ran `NG_DISABLE_VERSION_CHECK=1 npx @angular/cli@7 update @angular/cli@7 @angular/core@7`

> The update went smooth. No errors at all

# Meta

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.2.9.