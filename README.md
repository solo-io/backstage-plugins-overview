# Gloo Platform Portal Backstage Plugins

As a part of [Gloo Platform](https://www.solo.io/products/gloo-platform/), [Gloo Platform Portal](https://www.solo.io/products/gloo-portal/) provides a Kubernetes-native framework for managing the definitions of APIs, API client identity, and API policies that enables GitOps and CI/CD workflows. The portal abstracts the complexity and enables developers to publish, document, share, discover, and use APIs.

The Gloo Platform Portal Backstage plugins provide an interface for teams to manage, secure, and share APIs. This functionality is enabled through Gloo Platform Portal's built in REST API, and configurable ext-auth policies.

[See a demo of Gloo Platform Portal in action here](https://www.youtube.com/watch?v=YL1aqjZDqGQ&t=0)

## Plugin Types

Solo.io provides both a frontend and a backend plugin for Backstage. The main benefit of the frontend plugin is for teams to manage API keys from within the Backstage interface, with fine-grained user permissions that require a login. The backend plugin adds the benefit of integrating your Gloo Platform Portal APIs into your Backstage API catalog for a seamless view.

### Frontend Plugin

Installing the [frontend plugin](https://github.com/solo-io/platform-portal-backstage-plugin-frontend/tree/main/plugins/platform-portal-backstage-plugin-frontend#readme) creates a new tab in the Backstage sidebar where users can individually log in to the Gloo Platform Portal and access the following functionality:

- View OpenAPI docs for your Gloo Platform Portal APIs using Swagger UI and Redoc UI.
- View details about your Gloo Platform Portal API usage plans.
- View, create, and delete API keys for any of your usage plans.

### Backend Plugin

Installing the [backend plugin](https://github.com/solo-io/platform-portal-backstage-plugin-backend/tree/main/plugins/platform-portal-backstage-plugin-backend#readme) fetches your Gloo Platform Portal APIs on an interval and adds them to your Backstage catalog, along with some supporting entities like a `gloo-platform-portal-service-account` user.
