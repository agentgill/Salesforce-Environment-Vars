# Salesforce Environment Variables

A simple library for using Custom Metadata to manage simple Key/Value Environment variables

![UI Demo](https://user-images.githubusercontent.com/5217568/55663312-a63c4c00-57d9-11e9-994c-6e76ea0bd135.gif)

*idea inspired by Ralph Callaway's work*

## Usage

### install in org

[Use SFDX to deploy to org](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_build_mdapi_deploy.htm)

1. `git clone https://github.com/ChuckJonas/Salesforce-Environment-Vars.git`
1. `cd Salesforce-Environment-Vars`
1. `mkdir deploy`
2. `sfdx force:source:convert -d deploy/`
3. `sfdx force:mdapi:deploy -d deploy/ -u "YOUR_USERNAME_HERE" -l RunSpecifiedTests -r EnvTests`

**NOTE:** This application comes with a custom user interface for easier management of the ENV Vars. If you'd prefer not to use it, delete the following before deploying:

- `force-app/main/default/pages`
- `force-app/main/default/staticresources`

### Setup

If UI was installed, navigate to `/apex/env_vars` and setup your Environment Variables.  Otherwise, just manage like any other CustomMetadata.

#### Notes

The following types are currently supported:

- `String`
- `Integer`
- `Decimal`
- `Boolean`: Format: `true` or `false`
- `String[]`: Format: `["a","b","c"]`
- `Map<String,String>`: Format: `{"456":"xyz","123":"abc"}`

### Access in apex

Use `Env.get()` to access by passing in the `DeveloperName`:

``` java
// cast to datatype
Integer retries = (Integer) Env.get('Account_Sync_Retries');
String[] types = (String[]) Env.get('Status_Types');
```

### Contributing/Modifying

This project is built off the [B.A.S.S. Stack](https://github.com/ChuckJonas/bad-ass-salesforce-stack).  See Readme for details on how to develop.