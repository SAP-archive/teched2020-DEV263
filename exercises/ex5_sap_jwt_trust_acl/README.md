# Exercise 5 - Follow-up tasks due to deprecation of SAP_JWT_TRUST_ACL

This exercise is only relevant for communications between applications and/or services.

An operator needs no longer to maintain the ``SAP_JWT_TRUST_ACL`` environment variable with landscape specific values as part of the deployment descriptor (e.g. ``manifest.yml``).

Instead, if a business application A wants to call an application B, it is now mandatory that application B grants at least one scope to the calling business application A. Furthermore, business application A must accept these granted scopes or authorities as part of the application security descriptor.

## Exercise 5.1 Check prerequisites
So, Service/application B can get rid of ``SAP_JWT_TRUST_ACL`` environment variable, when using one of these client library versions:

- java-security >= 2.7.5
- spring-xsuaa
- container security api for node.js >= 3.0.6
- approuter >= 8.x
- sap_xssec for Python >= 2.1.0 

## Exercise 5.2 Fix security issue

With introduction of Audience validation as replacement for ``SAP_JWT_TRUST_ACL``, bypassing trust is no longer accepted. If you are using the wildcards ``*``, e.g.
 ```yml
env:
  SAP_JWT_TRUST_ACL: '[{"clientid":"*","identityzone":"*"}]
```

In that case the next steps are mandatory.
 
### Step 1 Grant scope(s) to calling app
For a business application A that wants to call an application B, it's now mandatory that the application /service B grants at least one scope to the calling business application A. 
You can grant scopes with the `xs-security.json` file. 

#### Communication with user principal
```
"scopes": [
	{
		"name"                 : "$XSAPPNAME.Read",
		"description"          : "read",
		"granted-apps"         : ["$XSAPPNAME(application,appa)" ] 
	}
]
```

#### Communication without user principal
```
"scopes": [
	{
		"name"                 : "$XSAPPNAME.Read",
		"description"          : "read",
		"grant-as-authority-to-apps" : ["$XSAPPNAME(application,appa)"]
	}
]
```

For additional information, refer to the [Application Security Descriptor Configuration Syntax](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html), in particular the sections [referencing the application](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb) and [authorities](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html#loio517895a9612241259d6941dbf9ad81cb__section_d1m_1nq_zy). 

### Step 2 Accept scopes
Furthermore, application A must accept these granted scopes /authorities in the authorities section of the xs-security.json. The configuration is done as part of the application security descriptor `xs-security.json` file.

#### Communication with user principal
```
"foreign-scope-references": ["$ACCEPT_GRANTED_SCOPES"],       
```
You can limit the references to those applications you want to accept. For example, `"foreign-scope-references": ["$XSAPPNAME(application,servb).Read"]`.

Furthermore, ensure that the application user has a role collection assigned that contains the role (based on the role template) with the required scope "$XSAPPNAME(application,servb).Read"]:

```json
  "role-templates": [
     ...
 
    {
      "name": "BusinessUser",
      "description": "Role Template for the Business User",
      "scope-references": [
        "uaa.user",
        "$XSAPPNAME(application,servb).Read"
      ]
    },
    ...
]
```

#### Communication without user principal
```
{
    "xsappname"     : "appa",
    "tenant-mode"   : "shared",
    "authorities":["$ACCEPT_GRANTED_AUTHORITIES"],
}
```
You can limit the references to those applications you want to accept. For example, `"authorities":["$XSAPPNAME(application,servb).Create"]`.

## Exercise 5.3 Re-deploy and test your application

To check whether your upgrade had no undesired side effects, deploy your application to Cloud Foundry and test.

## Summary

Having done that, you do not longer need to manage your `SAP_JWT_TRUST_ACL` environment variable and you do not longer accept any token from foreign applications.

Continue with the last exercise, [Exercise 6 - Prepare your multi-tenant application for new subaccounts](/exercises/ex6_tenantid), to prepare your application for new subaccounts.
