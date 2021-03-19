---
id: security
title: Security
sidebar_label: Security
slug: security
---

Once the task is created on **Scheduleapi** our platform then waits for the scheduled time to then send a request to your endpoint - such request will contain a unique token directly in the header to give you the ability to verify if such request is an authorized one or not. 

:::important

If the token does not correspond to the one that is shown by our request, please check if you've granted access to other third-parties. 
This will ensure that the calls that your endpoint is receiving are coming only allowed parties. 

:::

Each workspace has a unique token that, as mentioned before, will be sent in the header of each request 🔐

## Code examples

### Javascript

```js
// save the token somewhere safe, like the environment variables
const verificationToken = process.env.SCHEDULEAPI_TOKEN;
// Scheduleapi token is sent in the header
const sentToken = req.headers["scheduleapi-signature"];
// you have to check that they match
const tokensMatch = verificationToken === sentToken;
if (!tokensMatch) throw new Error("unauthorized");
```

---
