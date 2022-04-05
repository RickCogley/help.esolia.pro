---
title: PROdb Security Controls
date: 2022-04-05T09:55
description: Setting password, timeout and expiration policies.
order: 850
category: Service Details
tags:
  - PROdb
  - Password
  - Policies
---

# PROdb Security Controls

For PROdb enterprise subscribers who are using their own domain, it is possible for us to make security policy settings from "All Users", clicking the "Security Controls" button. For example, if your PROdb is hosted on db.ourdomain.com, the URLs for these functions would be: 

https://db.ourdomain.com/secure/accusers.aspx  
https://db.ourdomain.com/secure/accsecurity.aspx

These are the policies that can be set:

1. Password Complexity:
   * Minimum password length
   * Allowed password characters
1. Password expiration
1. Failed sign-in action
   * Don't block, or,
   * Block after N failures
1. Session Timeout

Each has different specific user impacts as follows.

## Password Complexity

Both length and allowed characters policy changes will take effect _on the next account password expiration_.

!!!success Note:
The minimal password length can be customized to a longer length than the maximum in the UI, for example to 12 or 14 characters. Please ask!   
!!!

## Password Expiration

Password expiration timeout policy change will take effect immediately. PROdb tracks the date of the last password change. The password expiration fact is calculated dynamically by adding a number of days to last change timestamp, and comparing with the current date. Any change will have immediate effect.

Specifically, PROdb uses a sliding expiration window for the authorization cookie that is saved by the user's browser. If we set the password expiration from nothing, to 90 days for example, if the user signs into the system with more than 45 days (half the period) until the expiration date, the system does nothing. Otherwise, the system will extend the expiration date for another 90 days.

## Failed sign-ins

A "Failed sign-ins" counter policy change will take effect on the next failed sign-in. The number of failed sign-ins in a row is counted, and if the number reaches the maximum, that account is locked. A successful sign-in or password reset clears the counter.

!!!success Note:
Locked user accounts can be unlocked from _All Users_.  
!!!

## Session Timeout

Changes to session timeout policy is a bit tricky. When a PROdb user signs in, an authorization "ticket" is created. Most of the ticket storage logic is handled by the Microsoft .NET framework that PROdb relies on, and PROdb simply checks if the user's sign-in is still valid, or redirects to the sign-in page automatically.

The sign-in ticket holds all the information necessary for security operations (issue date, timeout, expiration), so, any changes in policy settings are _not_ reflected in the ticket, unless it expires and is recreated, or, the user logs out and back in.

Any value for the "Session Timeout" policy other than "Never", leads to a "session cookie" being created and stored in the user's browser, (and also hides the "keep me logged in" option checkbox). This "session cookie" will expire:

* when specified by the policy (e.g. 8 hours, the maximum)
* when the user closes the last browser window or tab with PROdb open
* when the user restarts their computer

There is therefore a high likelihood that with the max 8 hours set, the user will need to re-sign-in once per day.

The challenge is, when the "Session Timeout" is set to "Never" _and_ the user selects "keep me logged in". In this case, the cookie is issued for one year, and the only way to get rid of it before the one year expiration, is to sign out.

Therefore, when changing policy from "Never" to some setting such as "8 hours", the best practice is to have users sign out so that the session cookie is re-created properly. 

!!!warning Important:
Session cookie recreation _cannot_ be automatically performed from the system side. Have users sign out and back in when changing this policy.  
!!!

![Figure: PROdb Security Controls Screen](/static/figure-prodb-security-controls-screen.png)