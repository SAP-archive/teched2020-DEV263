# SAP_JWT_TRUST_ACL is obsolete
It is no longer possible to use the `SAP_JWT_TRUST_ACL` parameter to specify a dedicated access control list (ACL) for JWT tokens. Changes also apply regarding the granting of security scopes, which are defined and granted in the application security descriptor (xs-security.json). For example, if a business application A wants to call an application B, it is now mandatory that application B grants at least one scope to the calling business application A. Furthermore business application A has to accept these granted scopes or authorities as part of the application security descriptor. For more information, see the release notes on Jam.

**TODO**https://jam4.sapjam.com/blogs/show/oEdyQO183plBoQdrvcPw2w

Communication Between Cloud Foundry Developments [DRAFT]
https://github.wdf.sap.corp/pages/CPSecurity/Knowledge-Base/03_ApplicationSecurity/Syntax%20and%20Semantics%20of%20xs-security.json/
https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/517895a9612241259d6941dbf9ad81cb.html
https://blogs.sap.com/2020/09/03/outdated-sap_jwt_trust_acl/


## Exercise 1.1 Sub Exercise 1 Description

After completing these steps you will have created...

1. Click here.
<br>![](/exercises/ex1/images/01_01_0010.png)

2.	Insert this line of code.
```abap
response->set_text( |Hello World! | ).
```



## Exercise 1.2 Sub Exercise 2 Description

After completing these steps you will have...

1.	Enter this code.
```abap
DATA(lt_params) = request->get_form_fields(  ).
READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc <> 0.
    response->set_status( i_code = 400
                     i_reason = 'Bad request').
    RETURN.
  ENDIF.

```

2.	Click here.
<br>![](/exercises/ex1/images/01_02_0010.png)


## Summary

You've now ...

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)
