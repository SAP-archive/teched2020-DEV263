# Exercise 1 - Check and upgrade approuter version

## Exercise 1.1 Check version
When you are using *approuter* ([npm](https://www.npmjs.com/package/@sap/approuter)), check whether you use a version < ``8.5``.

The approuter version can be found in the ``package.json``:
```
{
    "name": "approuter",
    "dependencies": {
        "@sap/approuter": "^6.1.0"
    },
    "scripts": {
        "start": "node node_modules/@sap/approuter/approuter.js"
    }
}
```

## Exercise 1.2 Upgrade version
Upgrade to the latest version.

> :bulb: Get a list of all available versions in npm: `npm view --registry https://npm.sap.com @sap/approuter versions`.

> :bulb: Consider the ``CHANGELOG.md`` in `node_modules/@sap/approuter`.


## Exercise 1.3 Deploy and test your approuter

To check whether your upgrade had no undesired side effects, deploy your approuter to Cloud Foundry and test.

## Summary

You've successfully upgraded the approuter version.

Depending on the programming language, your application is written, upgrade or migrate your Cloud Foundry applications one after the other to the latest Security client library version.

- [Exercise 2 - Check and upgrade Node.JS security libraries](/exercises/ex2_nodejs)
- [Exercise 3 - Check and upgrade SAP Java Buildpack and XSA Java Buildpack](/exercises/ex3_sapjavabuildpack)
- [Exercise 4 - Check and upgrade Java/Spring security libraries](/exercises/ex4_java)

## Further references
- [Authentication for Node.js Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/4902b6e66cbd42648b5d9eaddc6a363d.html)
- [Sample](https://github.com/SAP-samples/teched2019-cloud-cf-product-list/tree/teched2019/samples/approuter)
