# Exercise 6 - Prepare your application for new subaccounts
For NEW SCP subaccounts, it can no longer be guaranteed that “zone id” ==“subaccount id” == “tenant guid”. This is why you must make sure that 
- you use the `getSubaccountId()` method only if you need it for metering purposes (claim `ext_attr.subaccountid`). 
- you use the `getZoneId()` method as tenant discriminator (claim `zid`).


## Exercise 6.1 Check for occurrences of `getSubaccountId()` method
First make sure that you make use of the latest and recommended security client library version. You may must upgrade approuter or the security client libs provided for node.js, java and springboot as described [here](/README.md#exercises).

For each occurrence of `getSubaccountId()` method, check whether you need it for metering purposes? 
- If YES, you can keep that => nothing to do.
- If NO, you may use this information as tenant discriminator. In that case, replace it with `getZoneId()`. A Data migration is not required, as for existing subaccounts both methods `getSubaccountId()` and `getZoneId()` returns the same.


## Summary

You've now successfully prepared your application for new subaccounts where the tenant guid differs from the subaccount id and you've reached the end of the exercises!
