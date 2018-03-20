# SFDX  App

## Dev, Build and Test

This version of managed-pkg-0 is available to install via 04t46000000AKjrAAG.

If you would like to create your own version of the package, you can use 2gp to make your life easier, but deploying this as a 1gp would work just as well.

To create a 2gp package of this, change the `namespace` in `sfdx-project.json` to one linked to your dev hub and then run `sfdx force:package2:create` and use the resulting Package2 Id to replace `0Ho46000000TN1yCAG` in sfdx-project.json and in the following `sfdx force:package2:version:create` command.

```
sfdx force:package2:version:create -i 0Ho46000000TN1yCAG -w 60  --tag `git describe --long --dirty --always`  --branch    `git rev-parse --abbrev-ref HEAD | grep -v HEAD || \
    git describe --exact-match HEAD 2> /dev/null || \
    git rev-parse HEAD` --validateschema
```

## Resources


## Description of Files and Directories


## Issues


