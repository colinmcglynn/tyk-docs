---
date: 2017-03-23T16:15:37Z
title: Physical Key Expiry
menu:
  main:
    parent: "Your APIs"
weight: 5 
---


Tyk makes a distinction between a key expiring for an end user and a key physically expiring and being deleted.

When setting a key expiry on the session object, this will not affect whether the key is deleted or not. In fact, by default Tyk will not delete or expire a key.

However, in some cases it is preferable to have keys deleted - for example, so as not to clutter up your Redis DB with obsolete keys.

The way Tyk handles physical key deletion is in three stages:

1.  At the API level
2.  At the Global level
3.  A forced Global level

### Expiring Keys at the API level

In order to expire keys at the API level, all that is required is to set the `session_lifetime` field to an appropriate integer value in seconds.

The expiry will become effective when the key is no longer updated or used, so if a key has an expiry set of 24 hours, then the session expiry will only come into effect after this period has elapsed.

If this is not set, then the default is 0 seconds, which means the key will not be deleted from Redis.

### Expiring Keys at the Global level

If `session_lifetime` has not been set at the API level, it is possible to set a global expiration for all keys after the key's expiry time by setting `global_session_lifetime` in the `tyk.conf` file to an integer value in seconds. This value will only be active if the session lifetime has not been set. The session lifetime will always supersede the global lifetime.

### Forcing expiry at Global level

It is possible to override the session lifetime setting with the global lifetime setting by setting the `force_global_session_lifetime` to `true` in the `tyk.conf` file.

