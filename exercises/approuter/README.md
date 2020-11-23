# Exercise 1 Check and Upgrade Approuter Version

## Exercise 1.1 Upgrade version
In case you use one of the following client-libaries:

- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5

Upgrade to the latest version.

Consider the CHANGELOG.md in `node_modules/@sap/approuter`.

## Exercise 1.2 Leverage BoM
The versions of the SAP Java buildpack dependencies and the provided APIs from supported runtime containers, could be consumed through a Bill Of Materials (BoM). The BoM can be used to control the versions of a project’s dependencies.

https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6c6936e8e4ea40c9a9a69f6783b1e978.html

TODO explain (blocked by [this](https://github.com/SAP/cloud-security-xsuaa-integration/issues/400))
A sample can be found here: https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/samples/sap-java-buildpack-api-usage

## Exercise 1.3  Re-Deploy and test your application

TODO

## Summary

You've sucessfully upgraded the approutrer version.

Depending on the language, your application is written, upgrade / migrate your Cloud Foundry applications one after the other to the latest Security client library version.

- [Exercise 2 Node.JS](/exercises/nodejs)
- [Exercise 3 SAP Java Buildpack and XSA Java Buildpack](/exercises/sapjavabuildpack)
- [Exercise 4 Java / Spring](/exercises/java)
