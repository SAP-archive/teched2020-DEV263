# Exercise 5 Follow up tasks due to deprecation of SAP_JWT_TRUST_ACL

This exercise is only relevant for communications between applications / services with or without principal propagation.

An operator has no longer to maintain the environment parameter SAP_JWT_TRUST_ACL with landscape specific values as part of the deployment descriptor (e.g. manifest.yml).

Instead, if a business application A wants to call an application B, it is now mandatory that application B grants at least one scope to the calling business application A. Furthermore business application A has to accept these granted scopes or authorities as part of the application security descriptor.

## Exercise 5.1 Check Prerequisites
So, Service/Application B can get rid of SAP_JWT_TRUST_ACL environment variable, when using one of these client library versions:

- java-security >= 2.7.5
- spring-xsuaa
- container security api for node.js >= 3.0.6
- approuter >= 8.x
- sap_xssec for Python >= 2.1.0 

## Exercise 5.2 Fix Security Issue

With introduction of Audience Validation as replacement for SAP_JWT_TRUST_ACL, bypassing trust is no longer accepted. That means in case you make use of wildcards ``*``, e.g.
 ```yml
env:
  SAP_JWT_TRUST_ACL: '[{"clientid":"*","identityzone":"*"}]
```

 the next steps are mandatory.
 
### Step 1 Grant scope(s) to calling app
For a business application A that wants to call an application B, it's now mandatory that the application /service B grants at least one scope to the calling business application A. 
You can grant scopes with the `xs-security.json` file. 

#### Communication with User principal
```
"scopes": [
	{
		"name"                 : "$XSAPPNAME.Read",
		"description"          : "read",
		"granted-apps"         : ["$XSAPPNAME(application,appa)" ] 
	}
]
```

#### Communication with User principal
```
"scopes": [
	{
		"name"                 : "$XSAPPNAME.Read",
		"description"          : "read",
		"grant-as-authority-to-apps" : ["$XSAPPNAME(application,appa)"]
	}
]
```

For additional information, refer to the [Application Security Descriptor Configuration Syntax](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html), specifically the sections [referencing the application](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html#loio517895a9612241259d6941dbf9ad81cb__section_fm2_wsk_pdb) and [authorities](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html#loio517895a9612241259d6941dbf9ad81cb__section_d1m_1nq_zy). 

### Step 2 Accept scopes
Furthermore, the application A has to accept these granted scopes /authorities in the authorities section of the xs-security.json. The configuration is done as part of the application security descriptor xs-security.json file.

#### Communication with User principal
```
"foreign-scope-references": ["$ACCEPT_GRANTED_SCOPES"],       
```
You can limit the references to just those applications you want to accept. For example, `"foreign-scope-references": ["$XSAPPNAME(application,servb).Read"]`.

#### Communication without User principal
```
{
    "xsappname"     : "appa",
    "tenant-mode"   : "shared",
    "authorities":["$ACCEPT_GRANTED_AUTHORITIES"],
}
```
You can limit the references to just those applications you want to accept. For example, `"authorities":["$XSAPPNAME(application,servb).Create"]`.

## Summary

You've now ...

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)
