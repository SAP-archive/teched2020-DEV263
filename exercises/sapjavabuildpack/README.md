# Exercise 3 Cleanup APIs provided with SAP Java Buildpack and XSA Java Buildpack
This only applies to J2EE web applications securing their application with SAP Java Build Pack or XSA Java Buildpack.

As of **SAP Java Buildpack version 1.26.1** and as of **XSA Java Buildpack version 1.8.18** (XSA PL 129), the Java runtime provides the [*java-security*](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/java-security) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security). This is a fully compatible change, if you use Java Servlet Security only and the APIs provided by the Buildpack. Optionally you can leverage the latest API as announced with Release Note 2006A.

The SAP / XSA Java Buildpack no longer provide deprecated SAP-internal security libraries and no longer depends on Spring security / Jackson and Common Crypto Library.

## Exercise 3.1 Clean-up dependencies
In general, the APIs are kept compatible so we do not expect any incompatibilities. We recommend updating your `pom.xml` dependencies towards the open-source API in order to benefit from future API enhancements. For a step-by-step guide on how to replace your dependencies to the deprecated SAP-internal security libraries with the open-sourced ones, see Migration Guide for J2EE Web Applications that use SAP Java Buildpack for Securing their ApplicationsInformation published on non-SAP site.

https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/java-security/Migration_SAPJavaBuildpackProjects.md

## Leverage BOM
The versions of the SAP Java buildpack dependencies and the provided APIs from supported runtime containers, could be consumed through a Bill Of Materials (BOM). The BOM can be used to control the versions of a project’s dependencies.

https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6c6936e8e4ea40c9a9a69f6783b1e978.html

## Summary

You've now cleaned up dependencies to a deprecated library.

Continue to - [SAP_JWT_TRUST_ACL](../sap_jwt_trust_acl/README.md)

Or

[OPTIONAL] Continue to - [Exercise 3.2 Migration Guide to API Version 2](https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/java-security/Migration_SAPJavaBuildpackProjects_V2.md)
