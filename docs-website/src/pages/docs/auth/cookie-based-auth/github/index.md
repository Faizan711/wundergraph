---
title: GitHub
pageTitle: WunderGraph - Authentication - OIDC Providers - GitHub
description: Add GitHub authentication to your WunderGraph application.
---

{% callout %}
WunderGraph relies on OpenID Connect (OIDC) Identity Providers to be able to authenticate users.
{% /callout %}

Open your project's `wundergraph.config.ts` and scroll down to the `authentication` object.
Nested inside this is the `cookieBased` object, in which is a nested array called `providers`.
Inside this array, add a `github` auth provider as shown below:

```typescript
// wundergraph.config.ts
authentication: {
  cookieBased: {
    providers: [
      authProviders.github({
        id: 'github', // you have to choose this ID
        clientId: 'XXX', // client ID from GitHub
        clientSecret: 'XXX', // client secret from GitHub
      }),
    ];
  }
  // ...
}
```

Now create a [new OAuth app on GitHub](https://github.com/settings/applications/new).
You must supply an object inside the auth provider that contains three properties,
two of which come from your new GitHub OAuth App:

- `id`: your choice of unique id that identifies the provider (used to refer elsewhere to this specific provider)
- `clientId`: the client ID from GitHub
- `clientSecret`: the client secret from GitHub

{% callout type="warning" %}
Consider storing your IDs and secrets inside a `.env` file.
{% /callout %}
