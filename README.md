# Gloo Gateway Portal Backstage Plugin

The [Gloo Gateway](https://www.solo.io/products/gloo-platform/) developer portal provides a Kubernetes-native framework for managing the definitions of APIs, API client identity, and API policies that enables GitOps and CI/CD workflows. The portal abstracts the complexity and enables developers to publish, document, share, discover, and use APIs.

The [Gloo Gateway Portal Backstage backend plugin](https://github.com/solo-io/platform-portal-backstage-plugin-backend/tree/main/plugins/platform-portal-backstage-plugin-backend#readme) fetches your Gloo Platform Portal APIs on an interval and adds them to your Backstage catalog, along with some supporting entities like a `gloo-platform-portal-service-account` user. This functionality is enabled through Gloo Gateway Portal's built in REST API, and configurable ext-auth policies.
