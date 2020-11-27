# Exercise 4 - Check and Upgrade Java Security Libraries

> **Note** This is NOT relevant for applications that make use of Java Web security provided by SAP Java Buildpack (as described [here](https://github.com/SAP/cloud-security-xsuaa-integration#token-validation-for-java-web-applications-using-sap-java-buildpack)).

## Exercise 4.1 Upgrade versions
When you are using one of the following client-libaries:

- *Java* [*token-client*](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/token-client) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security.xsuaa) < 2.7.3
- [*java-security*](https://github.wdf.sap.corp/CPSecurity/java-container-security) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security) < 2.7.5

Upgrade to the latest version.

Consider [Release notes](https://github.com/SAP/cloud-security-xsuaa-integration/releases)

## Exercise 4.2 Check usage of deprecated container-security api library

The table below gives you an overview about the dependencies that needs to be replaced by the open-source version.

groupId (deprecated) | artifactId (deprecated) | groupId | artifactId
--- | --- | --- | --- 
com.sap.xs2.security | api | com.sap.cloud.security.xsuaa | api
com.sap.xs2.security | java-container-security | com.sap.cloud.security | java-security
com.sap.xs2.security | security-commons | ./. | ./. 
com.sap.cloud.security.xssec | api | com.sap.cloud.security.xsuaa | api
com.sap.cloud.security.xssec | security-commons | ./. | ./. 
com.sap.cloud.security.xsuaa | java-container-security-api | com.sap.cloud.security.xsuaa | api
com.sap.cloud.security.xsuaa | java-container-security | com.sap.cloud.security | java-security
com.sap.cloud.security.xsuaa | security-commons | ./. | ./. 
com.sap.security | nw.vsi | ./. | ./. 
com.sap.security.nw.sso.ntamd64.opt | sapjwt.ntamd64 | ./. | ./. 
com.sap.security.nw.sso.linuxx86_64.opt | sapjwt.linuxx86_64 | ./. | ./. 
com.sap.security.nw.sso.linuxppc64.opt | sapjwt.linuxppc64 | ./. | ./. 
com.sap.security.nw.sso.darwinintel64.opt | sapjwt.darwinintel64 | ./. | ./. 

In that case continue to [Exercise 4.2 Migrate java-container-security library](../java/migrationguides/README.md)

## Summary

You've now upgraded the version or detected a dependency to the SAP internal *container-security api for Java*, which is deprecated and must be replaced.

Continue with - [SAP_JWT_TRUST_ACL](/exercises/sap_jwt_trust_acl/README.md)


## Further references
- [Authentication for Java Resource Servers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5af489d4cfd54b0790a02e9f1425d57d.html)
