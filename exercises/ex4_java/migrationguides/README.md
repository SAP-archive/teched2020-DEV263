# Exercise 4.3 - Migrate java-container-security library

The `java-container-security` client depends on [Spring Security OAuth](https://projects.spring.io/spring-security-oauth), which has been set to maintenance with Spring 5. [Similar functions](https://spring.io/projects/spring-security-oauth) are now integrated (incompatible) in Spring Security ([communication from 2018](https://spring.io/blog/2018/01/30/next-generation-oauth-2-0-support-with-spring-security): "After Spring Security has reached feature parity with Spring Security OAuth, we will continue to support bugs and Security fixes for at least one year.")

This provides an overview about the different Java client libraries and the migration guides.
You need to select one.

![](images/java-container-security-migration-overview.png)

## Exercise 4.3.1 Select migration guide

### Migration Guide for Spring Boot applications
Recommended replacement for Spring 5 based applications is [spring-xsuaa](https://github.com/SAP/cloud-security-xsuaa-integration#token-validation-for-java-spring-boot-web-applications).

See [Migration Guide for Applications that use Spring Security and java-container-security](
https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/spring-xsuaa/Migration_JavaContainerSecurityProjects.md), which is located in ``SAP/cloud-security-xsuaa-integration`` repository.

### Migration Guide for (XSA) web applications using Spring-Security with less migration effort
If you like to have a smooth migration experience and like to stick to the Spring Security OAuth (deprecated), see [Migration Guide for Applications that use Spring Security and java-container-security](https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/java-security/Migration_SpringSecurityProjects.md), which is located in ``SAP/cloud-security-xsuaa-integration`` repository.

### Recommended replacement for native Java applications
Recommended replacement for Java native applications is [java-security](https://github.com/SAP/cloud-security-xsuaa-integration).

### Recommended replacement for J2EE applications
For J2EE applications, the recommended replacement would be the SAP Java Buildpack` or `XSA Java Buildpack`, which integrate Servlet Security into the tomcat server as described [here](https://github.com/SAP/cloud-security-xsuaa-integration#token-validation-for-java-web-applications-using-sap-java-buildpack).

## Exercise 4.3.2 Deploy and test your application

To check whether your migration had no undesired side effects, deploy your application to Cloud Foundry and test.


## Summary

You've successfully removed the dependency to the SAP internal *container-security api for Java*, which is deprecated and you have successfully replaced it by the open-source security client library, which is available on maven central.

Continue with - [Exercise 5 - Follow up tasks due to deprecation of SAP_JWT_TRUST_ACL](../sap_jwt_trust_acl/README.md).
