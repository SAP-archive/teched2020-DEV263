# Exercise 4 Check and Upgrade Java Security Libraries

## Exercise 4.1 Upgrade versions
In case you use one of the following client-libaries:

- *Java* [*token-client*](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/token-client) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security.xsuaa) < 2.7.3
- [*java-security*](https://github.wdf.sap.corp/CPSecurity/java-container-security) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security) < 2.7.5

Upgrade to the latest version.

Consider [Release Notes](https://github.com/SAP/cloud-security-xsuaa-integration/releases)

## Exercise Java 4.2 Check usage of deprecated container-security api library
You make use of SAP-internal java-container-security library? 

In that case continue to [Exercise Java 2: Migrate java-container-security library](../java/migrationguides/README.md)


## Further References
- [Authentication for Java Resource Servers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5af489d4cfd54b0790a02e9f1425d57d.html)
- https://github.com/sap-staging/cloud-authorization-client-library-java/tree/dcl-client-mockmwc-w-policies/samples/spring-security-cas-oauth2client#clone-repository-and-install-cas-client-libraries

