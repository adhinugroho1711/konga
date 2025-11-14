# Konga API Documentation

## Overview
Complete list of all available API endpoints in Konga v0.14.9

---

## Authentication Endpoints

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/register` | - | Display registration page (first-time setup) |
| POST | `/register` | AuthController | Register new user (first-time setup) |
| POST | `/login` | AuthController | User login |
| POST | `/login/:action` | AuthController | Login with action |
| POST | `/auth/local` | AuthController | Local authentication |
| POST | `/auth/local/:action` | AuthController | Local authentication with action |
| POST | `/auth/signup` | AuthController | User signup |
| GET | `/auth/activate/:token` | AuthController | Activate user account |
| GET/POST | `/auth/:provider` | AuthController | OAuth provider authentication |
| GET/POST | `/auth/:provider/callback` | AuthController | OAuth provider callback |
| GET/POST | `/auth/:provider/:action` | AuthController | OAuth provider with action |
| GET | `/logout` | AuthController | User logout |

---

## Application Pages

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Main dashboard/homepage |
| GET | `/404` | Not found page |
| GET | `/500` | Server error page |

---

## Snapshot Management

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| POST | `/api/snapshots/take` | SnapshotController | Create a new snapshot |
| POST | `/api/snapshots/snapshot` | SnapshotController | Snapshot operations |
| GET | `/api/snapshots/subscribe` | SnapshotController | Subscribe to snapshot updates |
| POST | `/api/snapshots/:id/restore` | SnapshotController | Restore from snapshot |
| GET | `/api/snapshots/:id/download` | SnapshotController | Download snapshot file |

---

## Kong Services Management

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/kongservices/tags` | KongServicesController | List all service tags |
| GET | `/api/kong_services/:id/consumers` | KongServicesController | Get consumers for a service |

---

## Kong Consumers Management

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/kong_consumers/:id/apis` | KongConsumersController | Get APIs for a consumer |
| GET | `/api/kong_consumers/:id/services` | KongConsumersController | Get services for a consumer |
| GET | `/api/kong_consumers/:id/routes` | KongConsumersController | Get routes for a consumer |

---

## Kong Routes Management

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/kong_routes/:id/consumers` | KongRoutesController | Get consumers for a route |

---

## Health Checks & Monitoring

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/kongnodes/healthchecks/subscribe` | KongNodeController | Subscribe to Kong node health checks |
| GET | `/api/apis/healthchecks/subscribe` | ApiHealthCheckController | Subscribe to API health checks |
| DELETE | `/api/healthchecks/reset` | ApiHealthCheckController | Reset health check data |

---

## Plugin Management

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/kong_plugins/list` | KongPluginsController | List all available Kong plugins |
| GET | `/api/schemas/authentication` | KongSchemasController | Get authentication schemas |

---

## User Management

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/user/:id/subscribe` | UserController | Subscribe to user updates |

---

## Settings & Configuration

| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/api/settings` | SettingsController | Get application settings |
| GET | `/api/settings/integrations` | SettingsController | Get integration settings |

---

## Kong Admin API Proxy

### Generic Proxy Routes
| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/kong` | KongProxyController | Kong root proxy |
| GET | `/kong/*` | KongProxyController | Proxy GET requests to Kong |
| POST | `/kong/*` | KongProxyController | Proxy POST requests to Kong |
| PUT | `/kong/*` | KongProxyController | Proxy PUT requests to Kong |
| PATCH | `/kong/*` | KongProxyController | Proxy PATCH requests to Kong |
| DELETE | `/kong/*` | KongProxyController | Proxy DELETE requests to Kong |

### Structured Proxy Routes (Kong 1.x)
| Method | Endpoint | Controller | Description |
|--------|----------|------------|-------------|
| GET | `/kong/:entity` | KongProxyController | List Kong entities |
| GET | `/kong/:entity/:id` | KongProxyController | Get specific Kong entity |
| GET | `/kong/:entity/:id/:child_entity` | KongProxyController | List child entities |

---

## Notes

### Kong Admin API Proxy
- All `/kong/*` routes are proxied to the configured Kong Admin API
- Supports full CRUD operations for all Kong entities:
  - Services
  - Routes
  - Consumers
  - Plugins
  - Certificates
  - Upstreams
  - Targets
  - And more...

### WebSocket Subscriptions
- Multiple endpoints support real-time updates via WebSocket subscriptions
- Health checks, snapshots, and user data can be monitored in real-time

### Authentication
- Most API endpoints require valid JWT token
- Some endpoints allow anonymous access during initial setup
- LDAP authentication is supported via the auth endpoints

---

*Generated from Konga v0.14.9 routes configuration*
