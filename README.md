# Gloo Platform Portal Backstage Plugin

As a part of [Gloo Platform](https://www.solo.io/products/gloo-platform/), [Gloo Platform Portal](https://www.solo.io/products/gloo-portal/) provides a Kubernetes-native framework for managing the definitions of APIs, API client identity, and API policies that enables GitOps and CI/CD workflows. The portal abstracts the complexity and enables developers to publish, document, share, discover, and use APIs.

The Gloo Platform Portal Backstage plugin provides an interface for teams to manage, secure, and share APIs. This functionality is enabled through Gloo Platform Portal's built in REST API, and configurable ext-auth policies.

[See a demo of Gloo Platform Portal in action here](https://www.youtube.com/watch?v=YL1aqjZDqGQ&t=0)

## Backstage Plugin Features

- View OpenAPI docs for your Gloo Platform Portal APIs using Swagger UI and Redoc UI.
- View details about your Gloo Platform Portal API usage plans.
- View, create, and delete API keys for any of your usage plans.

## Setup

1. Install the [Gloo Platform Portal Backstage plugin](https://www.npmjs.com/package/@solo.io/dev-portal-backstage-plugin) into your Backstage app:

```bash
yarn add --cwd packages/app @solo.io/dev-portal-backstage-plugin
```

2. In `./packages/app/src/App.tsx`, add these imports at the top of the file:

```tsx
import {
  GlooPortalHomePage,
  GlooPortalApiDetailsPage,
} from "@solo.io/dev-portal-backstage-plugin";
```

Then add these routes to the `<FlatRoutes/>` element in that file:

```tsx
<Route path="/gloo-platform-portal" element={<GlooPortalHomePage />} />
<Route path="/gloo-platform-portal/apis" element={<GlooPortalHomePage />} />
<Route path="/gloo-platform-portal/usage-plans" element={<GlooPortalHomePage />} />
<Route
  path="/gloo-platform-portal/apis/:apiId"
  element={<GlooPortalApiDetailsPage />}
/>
```

3. In `./packages/app/src/components/Root/Root.tsx`, add these imports to the top of the file:

```tsx
import { GlooIcon } from "@solo.io/dev-portal-backstage-plugin";
```

Then add this to the `<SidebarScrollWrapper/>` element in that file.

```tsx
<SidebarItem icon={GlooIcon} to="gloo-platform-portal" text="Gloo Portal" />
```

4. Set the following variables in your `app-config.local.yaml` file to match your Gloo Platform Portal and Keycloak setup before running Backstage:

```yaml
glooPlatformPortal:
  # The URL of the Gloo Platform Portal REST server.
  # The value of this variable should be: <portal-server-url>/v1
  # The default value is: "http://localhost:31080/v1".
  portalServerUrl: "http://localhost:31080/v1"

  # The oauth client id.
  # In keycloak, this is shown in the client settings
  # of your keycloak instances UI: <your-keycloak-url>/auth
  clientId: ""

  # This is the endpoint to get the oauth token.
  # In keycloak, this is the `token_endpoint` property from:
  # <your-keycloak-url>/auth/realms/<your-realm>/.well-known/openid-configuration
  tokenEndpoint: ""

  # This is the endpoint to get PKCE authorization code.
  # In keycloak, this is the `authorization_endpoint` property from:
  # <your-keycloak-url>/auth/realms/<your-realm>/.well-known/openid-configuration
  authEndpoint: ""

  # This is the endpoint to end your session.
  # In keycloak, this is the `end_session_endpoint` property from:
  # <your-keycloak-url>/auth/realms/<your-realm>/.well-known/openid-configuration
  logoutEndpoint: ""
```

## Screenshots

Logged out view:

![logged out](./readme_assets/logged-out.png)

Logged in view:

![logged in](./readme_assets/logged-in.png)

Viewing a list of APIs:

![API list](./readme_assets/apis.png)

Viewing an API using an OpenAPI schema viewer:

![API details](./readme_assets/api-details.png)

Viewing API usage plans:

![usage plans and api keys](./readme_assets/usage-plans.png)

Generating a new API key under a usage plan:

![generating a new api key](./readme_assets/generate-new-key.png)
