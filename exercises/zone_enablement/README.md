# Exercise 6 Prepare your application for zone-enabled subaccounts
For NEW SCP subaccounts it can no longer be guaranteed, that “zone id” ==“subaccount id” == “tenant guid”. That’s why you have to make sure, that you use the `getSubaccountId()` method only in case you need it for metering purposes (claim `ext_attr.subaccountid`). And that you use the `getZoneId()`method as tenant discriminator (claim `zid`).


## Exercise 6.1 Check for occurrences of `getSubaccountId()` method
First make sure, that you make use of the latest and recommended security client library version. You may have to upgrade approuter, or the security client libs provided for node.js, java and springboot as described [here](/README.md#exercises).

For each occurence of `getSubaccountId()` method, check whether you required that for metering purposes? 
- If YES, then you can keep that => nothing to do.
- If NO, you may used that information as tenant discriminator. In that case, replace it with `getZoneId()`. A data migration is not required, as for existing subaccounts both methods `getSubaccountId()` and `getZoneId()` returns the same.


## Summary

You've now succesfully prepared your application for zone-enabled subaccounts and you've reached the end of the exercises!
