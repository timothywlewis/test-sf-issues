# sfdx pull subscriber edited CustomMetadata record

This is to demonstrate the issue for [Partner Case 18583564][1]
which was first [posted to SFDX Trailblazer community][2].

Here is a video walkthrough of the issue and it's workaround: https://youtu.be/y27jtpOw5ME

[1]: https://partners.salesforce.com/partnerCaseDetails?id=5000M00000jth6JQAQ
[2]: https://success.salesforce.com/0D53A00003TuBxk

## Test

```
sfdx force:org:create -f ./config/project-scratch-def.json -s -a test-edit-a-custom-metadata-record-0
# install managed-pkg-0 which is in namespace asldkjasldkfjas
sfdx force:package:install -p 10 -w 10 -i 04t46000000AKjrAAG
sfdx force:org:open
# Setup > Custom Metadata Types > MyCMT > Manage Records > Edit MyPackagedRecord
sfdx force:source:pull
# Expect it to retrieve asldkjasldkfjas__MyCMT.asldkjasldkfjas__MyRecord but instead it displays
# ERROR: Entity of type 'CustomMetadata' named "asldkjasldkfjas__MyCMT.MyRecord" cannot be found.
```

## Workaround

Clone the customMetadata record in the scratch org and then `sfdx force:source:pull` will download the no-namespace version of the record into the sfdx project (e.g. `asldkjasldkfjas__MyCMT.MyRecord.md-meta.xml`). Rename the record to add the namespace of the managed package (rename `asldkjasldkfjas__MyCMT.MyRecord.md-meta.xml` to `asldkjasldkfjas__MyCMT.asldkjasldkfjas__MyRecord.md-meta.xml`) and then `sfdx force:source:push` will upload it back to the org.
