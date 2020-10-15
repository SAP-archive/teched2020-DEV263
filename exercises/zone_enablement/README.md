# Exercise 6 Prepare your application for zone-enabled subaccounts
For NEW SCP subaccounts it can no longer be guaranteed, that “zone id” ==“subaccount id” == “tenant guid”. That’s why you must make sure, that you use the `getSubaccountId()` method only in case you need it for metering purposes (claim `ext_attr.subaccountid`). And that you use the `getZoneId()`method as tenant discriminator (claim `zid`).


## Exercise 6.1 Check for occurrences of `getZoneId()` method
TODO

## Summary

You've now ...

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)
