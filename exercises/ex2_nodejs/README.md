# Exercise 2 - Check and upgrade Node.JS security libraries

## Exercise 2.1 Upgrade version
When you are using one of the following client libraries:

- *SAP container security api for Node.JS* ([npm](https://www.npmjs.com/package/@sap/xssec)) < 3.0.6

Upgrade to the latest version.

> :bulb: Get a list of all available versions in npm: `npm view --registry https://npm.sap.com @sap/xssec versions`

> :bulb: Consider the ``CHANGELOG.md`` in `node_modules/@sap/xssec`.

#### If you upgrade from version 2.x.x
For most users, the @sap/xssec 3.x.x library is backward compatible to the 2.x.x versions. Especially if you use the documented methods only, you are safe.

But if you directly use member attributes of the so called `SecurityContext` and you do not get them using `getter` function, you must be aware of the fact that these attributes are now "private" and only available using the documented getter method.

For example:
```js
  var token = userContext.token; // will be undefined in version 3.x.x
  
  // use the documented way instead
  var token = userContext.getAppToken();
```

## Exercise 2.2 Deploy and test your application

To check whether your upgrade had no undesired side effects, deploy your application to Cloud Foundry and test.

## Summary

You've successfully upgraded the *container-security api for Node.js*.

Continue with - [Exercise 5 - Follow-up tasks due to deprecation of SAP_JWT_TRUST_ACL](/exercises/ex5_sap_jwt_trust_acl/README.md).

## Further references
- [Authentication for Node.js Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/4902b6e66cbd42648b5d9eaddc6a363d.html)
- [Node.js Application Sample](https://github.com/SAP-samples/teched2019-cloud-cf-product-list/tree/teched2019/samples/nodejs)
