# DEV263 - Secure Cloud Applications by Default – Assisted Migration

## Description

This repository contains the material for the SAP TechEd 2020 session called Session ID - Session Title. 

## Overview

This session introduces attendees to...

## Requirements
The requirement to follow the migration exercises in this repository are to check whether you make use of one of these security libraries / versions. Only in these cases, an version upgrade / a migration is of relevance.

### Java Development
- SAP internal *container-security api for Java* which was provided with [XS_JAVA 2.0.05](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.05/en-US/6511bc054b0e48369a625a8019fefd53.html)
- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5
- *Java* [*token-client*](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/token-client) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security.xsuaa) < 2.7.3
- [*java-security*](https://github.wdf.sap.corp/CPSecurity/java-container-security) library [maven central](https://search.maven.org/search?q=g:com.sap.cloud.security) < 2.7.5
- *xs-user-holder* [maven central](https://search.maven.org/search?q=g:com.sap.cloud.sjb) < 1.17.5
- *SAP Cloud SDK* [maven central](https://search.maven.org/search?q=g:com.sap.cloud.sdk) < 3.25.0
- *SAP Java Buildpack* < 1.26
- *XSA Java Buildpack* < 1.8.18 was released with XSA PL 129

### Node.JS Development
- *SAP container security api for Node.JS* [npm](https://www.npmjs.com/package/@sap/xssec) < 3.0.6
- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5

### Python Development
- *Python sap_xssec* < 2.1.0
- *approuter* [npm](https://www.npmjs.com/package/@sap/approuter) < 8.5


## Exercises

Provide the exercise content here directly in README.md using [markdown](https://guides.github.com/features/mastering-markdown/) and linking to the specific exercise pages, below is an example.

- [Getting Started](exercises/ex0/)
- [Exercise 1 - First Exercise Description](exercises/ex1/)
    - [Exercise 1.1 - Exercise 1 Sub Exercise 1 Description](exercises/ex1#exercise-11-sub-exercise-1-description)
    - [Exercise 1.2 - Exercise 1 Sub Exercise 2 Description](exercises/ex1#exercise-12-sub-exercise-2-description)
- [Exercise 2 - Second Exercise Description](exercises/ex2/)
    - [Exercise 2.1 - Exercise 2 Sub Exercise 1 Description](exercises/ex2#exercise-21-sub-exercise-1-description)
    - [Exercise 2.2 - Exercise 2 Sub Exercise 2 Description](exercises/ex2#exercise-22-sub-exercise-2-description)


**OR** Link to the PDF document stored in your github repo for example...

Start the exercises [here](exercises/myPDFDoc.pdf).
    
**OR** Link to the Tutorial Navigator for example...

Start the exercises [here](https://developers.sap.com/tutorials/abap-environment-trial-onboarding.html).

**IMPORTANT**

Your repo must contain the .reuse and LICENSES folder and the License section below. DO NOT REMOVE the section or folders/files. Also, remove all unused template assets(images, folders, etc) from the exercises folder. 

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (c) 2020 SAP SE or an SAP affiliate company. All rights reserved. This file is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
