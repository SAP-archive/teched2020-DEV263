# Exercise 3 - Check and upgrade SAP Java Buildpack and XSA Java Buildpack

This only applies to J2EE web applications securing their application with SAP Java Buildpack or XSA Java Buildpack.

As of **SAP Java Buildpack version 1.26.1** and as of **XSA Java Buildpack version 1.8.18** (XSA PL 129), the Java runtime provides the open source [*java-security*](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/java-security) library from [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security). This is a fully compatible change if you use Java Servlet Security only and the APIs provided by the Buildpack. Optionally you can leverage the latest API as announced with release note 2006A.

The SAP and XSA Java Buildpack no longer provide deprecated SAP-internal Security libraries and no longer depends on Spring Security / Jackson and Common Crypto Library.

## Exercise 3.1 Clean-up dependencies
In general, the APIs are kept compatible. For this reason we do not expect any incompatibilities. We recommend that you update your `pom.xml` dependencies towards the open-source API in order to benefit from future API enhancements. For a step-by-step guide on how to replace your dependencies to the deprecated SAP-internal security libraries with the open-sourced ones, see [Migration Guide for J2EE Web Applications that use SAP Buildpack for securing their Applications](https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/java-security/Migration_SAPJavaBuildpackProjects.md) which is located in ``SAP/cloud-security-xsuaa-integration`` repository.


## Exercise 3.2 Leverage BOM
The versions of the SAP Java buildpack dependencies and the provided APIs from supported runtime containers, could be consumed through a Bill of Materials (BOM). Use the BOM to control the versions of a project’s dependencies as described [here on help.sap.com](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6c6936e8e4ea40c9a9a69f6783b1e978.html). 


## Exercise 3.3 Deploy and test your application

To check whether your upgrade had no undesired side effects, deploy your application to Cloud Foundry and test.


## Summary

You've successfully removed the dependency to the SAP internal *container-security api for Java*, which is deprecated and you have successfully replaced it with the open-source security client library, which is available on maven central.

Optionally continue with - [Migration Guide for J2EE Web Applications that use SAP Buildpack for securing their applications - API Version 2](https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/java-security/Migration_SAPJavaBuildpackProjects_V2.md) which is located in SAP/cloud-security-xsuaa-integration repository.


Or

Continue with - [Exercise 5 - Follow-up tasks due to deprecation of SAP_JWT_TRUST_ACL](../ex5_sap_jwt_trust_acl/README.md)


## Further references
- [Configuring Authentication for SAP Java Buildpacks](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ead7ee64f96f4c42bacbf0ae23d4135b.html)
- [Sample](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/samples/sap-java-buildpack-api-usage)
