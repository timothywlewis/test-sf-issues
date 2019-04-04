# SFDX App

RE: Support Case 22274200 - https://partners.salesforce.com/partnerCaseDetails?id=5000M00000oD9oLQAS

## Dev, Build and Test

Installation URL: https://test.salesforce.com/packaging/installPackage.apexp?p0=04t460000023fDdAAI

e.g. https://ability-platform-8684-dev-ed--asldkjasldkfjas.visualforce.com/apex/TestVF

## Resources

## Description of Files and Directories

To create the 04t package, the following was executed:

```
sfdx force:package:create -t Managed -n test-sf-issues-1 -r force-app
sfdx force:package:version:create -d force-app -x
```

## Issues
