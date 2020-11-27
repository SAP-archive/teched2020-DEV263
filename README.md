# DEV263 - Secure Cloud Applications by Default – Assisted Migration

## Description

This repository contains the material for the SAP TechEd 2020 session called DEV263 - Secure Cloud Applications by Default. 

## Overview

This session walks the attendees through the process of upgrading the client libraries and migrating to them. 

This course is mainly targeted to application developers that needs to upgrade their existing application to be up-to-date and ready for upcoming features.

## Prerequisites
Check whether you make use of one of these security libraries / versions.

#### Java development
- SAP internal *container-security api for Java* which was provided with [XS_JAVA 2.0.05](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.05/en-US/6511bc054b0e48369a625a8019fefd53.html)
- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5
- *Java* [*token-client*](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/token-client) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security.xsuaa) < 2.7.3
- [*java-security*](https://github.wdf.sap.corp/CPSecurity/java-container-security) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security) < 2.7.5
- *xs-user-holder* [maven central](https://search.maven.org/search?q=g:com.sap.cloud.sjb) < 1.17.5
- *SAP Cloud SDK* [maven central](https://search.maven.org/search?q=g:com.sap.cloud.sdk) < 3.25.0
- *SAP Java Buildpack* < 1.26
- *XSA Java Buildpack* < 1.8.18 was released with XSA PL 129

#### Node.JS development
- *SAP container security api for Node.JS* [npm](https://www.npmjs.com/package/@sap/xssec) < 3.0.6
- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5

#### Python development
- *Python sap_xssec* < 2.1.0
- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5

## Before you start
Before upgrade, review these general changes and the library specific release notes, especially if you want to upgrade major versions.

### Security vulnerabilities
Please upgrade to the latest security client library version. This upgrade fixes known security vulnerabilities.

 
### SAP_JWT_TRUST_ACL is obsolete
It is no longer possible to use the `SAP_JWT_TRUST_ACL` parameter to specify a dedicated access control list (ACL) for JWT tokens. Changes also apply regarding the granting of security scopes, which are defined and granted in the application security descriptor (xs-security.json). For example, if a business application A wants to call an application B, it is now mandatory that application B grants at least one scope to the calling business application A. Furthermore, business application A must accept these granted scopes or authorities as part of the application security descriptor.

[Release note, September 24th 2020](https://help.sap.com/doc/43b304f99a8145809c78f292bfc0bc58/Cloud/en-US/98bf747111574187a7c76f8ced51cfeb.html?sel1=Authorization%20and%20Trust%20Management&date=all&from=2020-09-24&to=2020-09-24)
 
### User token is replaced with JWT bearer token grant type
We want to inform you that the proprietary user token flow of UAA has been replaced by the [JWT bearer token grant flow](https://docs.cloudfoundry.org/api/uaa/version/74.26.0/index.html#jwt-bearer-token-grant).

The “uaa.user” scope and an additional roundtrip is not required anymore. All client libraries that support token exchange, make use of the JWT bearer token grant flow. When using one the client libraries listed above to perform the token exchange, upgrade to the latest version and you’re done. 

> Please note that JWT bearer token response provides NO refresh_token. This is no incompatible change, as it was never exposed via the API.
 
### getSubaccountId vs. getIdentityZone vs. getZoneId
In order to prepare for the possibility to decouple subaccount (metering) and the XSUAA tenant (zone id), we explicitly added `getZoneId()` next to `getSubaccountId()`.
 
For NEW SAP Cloud Platform subaccounts, it can no longer be guaranteed that “zone id” == “subaccount id” == “tenant guid”. That’s why you must make sure that you use the `getSubaccountId()` method provided that you need it for metering purposes (claim `ext_attr.subaccountid`). And that you use the `getZoneId()` method as tenant discriminator (claim `zid`).


### Java-container-security Xsuaa client library is deprecated
As of begin of July, SAP-internal java-container-security library is deprecated. We recommend that you replace Spring (Boot) based applications with spring-xsuaa. SAP Java Buildpack is the recommendation for J2EE applications and java-security is the library to use for token-validation for native Java applications. You can find more details and the migration guides linked [here](exercises/java/migrationguides).

[Release note, July 2nd 2020](https://help.sap.com/viewer/12a72dd465d240d9bc4988ce6c691271/Cloud/en-US)

 
### SAP Java Buildpack and XSA Java Buildpack  
As of SAP Java Buildpack version 1.26. and as of XSA Java Buildpack version 1.8.18 ( XSA PL 129), the Java runtime provides the [java security library apis](https://github.com/SAP/cloud-security-xsuaa-integration) that are available on maven central. This is a fully compatible change if you use Java Servlet Security only and the APIs provided by the buildpack. Optionally you can leverage the latest API as announced with the release notes. 

[SAP Java Buildpack, Version 1.26.1 - Release note, 2 July 2020](https://help.sap.com/doc/43b304f99a8145809c78f292bfc0bc58/Cloud/en-US/98bf747111574187a7c76f8ced51cfeb.html?from=2020-07-02&to=2020-07-02)  
[SAP HANA Platform SPS 03 Release note](https://launchpad.support.sap.com/#/notes/2551355)  
[SAP HANA Platform SPS 04 Release note](https://launchpad.support.sap.com/#/notes/2656575)  


## Exercises
- [Exercise 1 Approuter - Upgrade Security Client Lib Version](exercises/approuter)
- [Exercise 2 Node.JS - Upgrade Security Client Lib Version](exercises/nodejs)
- [Exercise 3 SAP Java Buildpack and XSA Java Buildpack - Adapt Dependencies](exercises/sapjavabuildpack)
- [Exercise 4 Java / Spring - Upgrade Security Client Lib Version](exercises/java)
- [Exercise 5 SAP_JWT_TRUST_ACL](exercises/sap_jwt_trust_acl)
- [Exercise 6 Prepare for New Subaccounts](exercises/zone_enablement)


## How to obtain support
Support for the content in this repository is available during the TechEd 2020 event for which this content has been designed. Otherwise, you can request support via the [Issues](../../issues) tab.

## License
Copyright (c) 2020 SAP SE or an SAP affiliate company. All rights reserved. This file is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
