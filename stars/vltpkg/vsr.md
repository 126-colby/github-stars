---
project: vsr
stars: 187
description: a minimal npm-compatible package registry
url: https://github.com/vltpkg/vsr
---

**vlt** serverless registry (`vsr`)
===================================

`vsr` aims to be a minimal "npm-compatible" registry which replicates the core features found in `registry.npmjs.org` as well as adding net-new capabilities.

**Table of Contents:**

-   Quick Starts
-   Requirements
-   API
-   Compatibility
-   Comparisons
-   Roadmap
-   License

### Quick Starts

#### Local

You can quickly get started by installing/executing `vsr` with the following command:

npx -y vltpkg/vsr

#### Production

You can deploy `vsr` to Cloudflare in under 5 minutes, for free, with a single click (coming soon).

Alternatively, you can deploy to production using `wrangler` after following the **Development** quick start steps.

#### Development

# clone the repo
git clone https://github.com/vltpkg/vsr.git

# navigate to the repository directory
cd ./vsr

# install the project's dependencies
npm install

# run tbe development script
npm run dev

### Requirements

#### Production

-   Cloudflare (free account at minimum)
    -   Workers (free: 100k requests /day)
    -   D1 Database (free: 100k writes, 5M reads /day & 5GB Storage /mo)
    -   R2 Bucket (free: 1M writes, 10M reads & 10GB /mo)

> Note: all usage numbers & pricing documented is as of **October 24th, 2024**. Plans & metering is subject to change at Cloudflare's discretion.

#### Development

-   `git`
-   `node`
-   `npm`

### Granular Access Tokens

All tokens are considered "granular access tokens" (GATs). Token entries in the database consist of 3 parts:

-   `token` the unique token value
-   `uuid` associative value representing a single user/scope
-   `scope` value representing the granular access/privileges

#### `scope` as a JSON `Object`

A `scope` contains an array of privileges that define both the type(s) of & access value(s) for a token.

Note

Tokens can be associated with multiple "types" of access

-   `type(s)`:
    -   `pkg:read` read associated packages
    -   `pkg:read+write` write associated packages (requires read access)
    -   `user:read` read associated user
    -   `user:read+write` write associated user (requires read access)
-   `value(s)`:
    -   `*` an ANY selector for `user:` or `pkg:` access types
    -   `~<user>` user selector for the `user:` access type
    -   `@<scope>/<pkg>` package specific selector for the `pkg:` access type
    -   `@<scope>/*` glob scope selector for `pkg:` access types

Note

-   user/org/team management via `@<scope>` is not supported at the moment

Scope Examples

##### End-user/Subscriber Persona

-   specific package read access
-   individual user read+write access

\[
  {
    "values": \["@organization/package-name"\],
    "types": {
      "pkg": {
        "read": true,
      }
    }
  },
  {
    "values": \["~johnsmith"\],
    "types": {
      "user": {
        "read": true,
        "write": true,
      }
    }
  }
\]

##### Team Member/Maintainer Persona

-   scoped package read+write access
-   individual user read+write access

\[
  {
    "values": \["@organization/\*"\],
    "types": {
      "pkg": {
        "read": true
      }
    }
  },
  {
    "values": \["~johnsmith"\],
    "types": {
      "user": {
        "read": true,
        "write": true,
      }
    }
  }
\]

##### Package Publish CI Persona

-   organization scoped packages read+write access
-   individual user read+write access

\[
  {
    "values": \["@organization/package-name"\],
    "types": {
      "pkg": {
        "read": true
      }
    }
  },
  {
    "values": \["~johnsmith"\],
    "types": {
      "user": {
        "read": true,
        "write": true,
      }
    }
  }
\]

##### Organization Admin Persona

-   organization scoped package read+write access
-   organization users read+write access

\[
  {
    "values": \["@company/\*"\],
    "types": {
      "pkg": {
        "read": true,
        "write": true
      },
      "user": {
        "read": true,
        "write": true
      }
    }
  }
\]

##### Registry Owner/Admin Persona

\[
  {
    "values": \["\*"\],
    "types": {
      "pkg": {
        "read": true,
        "write": true
      },
      {
        "user": {
          "read": true,
          "write": true
        }
      }
    }
  }
\]

### API

We have rich, interactive API docs out-of-the-box with the help of our friends Scalar. The docs can be found at the registry root when running `vsr` locally (ex. run `npx -y vltpkg/vsr` &/or check out this repo & run `npm run dev`)

### `npm` Client Compatibility

The following commands should work out-of-the-box with `npm` & any other `npm` "compatible" clients although their specific commands & arguments may vary (ex. `vlt`, `yarn`, `pnpm` & `bun`)

#### Configuration

To use `vsr` as your registry you must either pass a registry config through a client-specific flag (ex. `--registry=...` for `npm`) or define client-specific configuration which stores the reference to your registry (ex. `.npmrc` for `npm`). Access to the registry & packages is private by default although an `"admin"` user is created during setup locally (for development purposes) with a default auth token of `"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"`.

; .npmrc
registry\=http://localhost:1337
//localhost:1337/:\_authToken\=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

#### Supported `npm` Commands

-   ✅ implemented
-   ⏳ in progress
-   🕤 planned to support

Support

Commannd

✅

`access`

✅

`access list packages`

✅

`access get status`

❌

`access set status`

❌

`access set mfa`

❌

`access grant`

❌

`access revoke`

🕤

`adduser` - `PUT /-/org/@<org>/<user>`: Adds/updates a user (requires admin privileges)

❌

`audit`

✅

`bugs`

❌

`dist-tag add`

❌

`dist-tag rm`

❌

`dist-tag ls`

✅

`deprecate`

✅

`docs`

✅

`exec`

❌

`hook`

✅

`install`

❌

`login`

❌

`logout`

❌

`org`

✅

`outdated`

❌

`owner add`

❌

`owner rm`

❌

`owner ls`

✅

`ping`

❌

`profile enable-2fa`

❌

`profile disable-2fa`

✅

`profile get`

🕤

`profile set` - `PUT /-/npm/v1/user`: Updates a user (requires auth)

✅

`publish`

✅

`repo`

❌

`search`

❌

`star`

❌

`team`

✅

`view`

✅

`whoami`

-   ✅ supported
-   ❌ unsupported

### Comparisons

Feature

`vsr`

`verdaccio`

`jsr`

Serverless

✅

❌

❌

JavaScript Backend

✅

✅

❌

Granular Access/Permissions

✅

✅

❌

Proxy Upstream Registries

⏳

✅

❌

Unscoped Package Names

✅

✅

❌

npm Package Publishing

✅

✅

❌

npm Package Installation

✅

✅

✅\*

CDN

🕤

❌

✅

ESM

🕤

❌

✅

Manifest Validation

✅

❌

❌

Plugins

⏳

✅

❌

Events/Hooks

🕤

✅

❌

Programmatic API

❌

✅

❌

Web Interface

🕤

✅

✅

Search

🕤

✅

✅

First-Class Typescript

❌

❌

✅

API Documentation Generation

❌

❌

✅

Multi-Cloud

🕤

✅

✅

**Azure DevOps Artifacts** Upstream

✅

✅

✅

**JFrog Artifactory** Upstream

✅

✅

❌

**Google Artifact Registry** Upstream

✅

✅

❌

> `*` requires `jsr`\-specific tooling or use a modified package name when using traditional npm clients (ref. https://jsr.io/docs/npm-compatibility)

### Roadmap

Status

Feature

✅

api: minimal package metadata

✅

api: full package manifests

✅

api: publishing private, scoped packages

✅

api: package manifest validation

✅

api: admin user management (add/update/remove users)

✅

api: user token management (add/update/remove tokens)

✅

web: docs portal

✅

api: unscoped packages

⏳

web & api: custom dist-tags (`latest` is supported)

⏳

web & api: token rate-limiting

🕤

web & api: search

🕤

web & api: staging

🕤

web: admin user management

🕤

web: user registration

🕤

web: user login (ex. `npm login` / `--auth-type=web`)

🕤

web: user account management

### License

This project is licensed under the Functional Source License (**FSL-1.1-MIT**).
