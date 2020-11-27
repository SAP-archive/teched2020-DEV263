# Exercise 6 - Prepare your multi-tenant application for new subaccounts
For NEW SAP Cloud Platform subaccounts, the aspect of multi-tenancy must be decoupled from the aspects of subaccounts. Both aspects may have different IDs: The subaccount ID keeps identifying the subaccount. The new zone ID identifies the tenant for data isolation and identity and access management.

This is why you must make sure that 
- you use the `getSubaccountId()` method only if you need it for metering or billing purposes (`ext_attr.subaccountid` claim). 
- you use the `getZoneId()` method instead of `getSubaccountId()` or `getIdentityZone()` method as tenant discriminator as key for data isolation between tenants (`zid` claim).

## Exercise 6.1 Check for occurrences of `getSubaccountId()` and `getIdentityZone()` method
First make sure that you make use of the latest and recommended security client library version. You may must upgrade approuter or the security client libs provided for node.js, java and springboot as described [here](/README.md#exercises).

For each occurrence of `getSubaccountId()` or `getIdentityZone()` method, check whether you need it for metering or billing purposes? 
- If YES, you can keep that => nothing to do.
- If NO, you may use this information as tenant discriminator. In that case, replace it with `getZoneId()`. A Data migration is not required, as for existing subaccounts both methods `getSubaccountId()` and `getZoneId()` returns the same.


## Summary

You've now successfully prepared your application for new subaccounts where the tenant guid differs from the subaccount id and you've reached the end of the exercises!
