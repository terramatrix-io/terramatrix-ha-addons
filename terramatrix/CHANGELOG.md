# Changelog

## 2.0.2

- `cloud_url` is now accepted as typed: `Https://…` and a trailing slash both
  work. Before, a capital letter in the scheme or a trailing slash made every
  connection attempt fail with a bare "websocket error".
- An unusable `cloud_url` now stops the add-on with a message that names the
  setting, instead of retrying forever.

## 2.0.1

- TerraMatrix now shows the correct entity count. The add-on reported its
  readiness before Home Assistant had finished loading, so the count read 0.

## 2.0.0

- Replaced the bridge with the TerraMatrix edge runtime. It connects to the
  TerraMatrix workflow service over TNCP instead of the backend `/ha-bridge`
  socket.
- Configuration changed: set `node_id`, `enrollment_token` and `cloud_url`
  (from TerraMatrix: Settings, Integrations, Home Assistant, New token). The
  old `cloud_token` and `standalone_mode` options are gone; 1.x tokens do not
  work with 2.0.0.
- armv7 is no longer supported.

## 0.1.5

- Automation delete now verifies the removal actually took effect and reports YAML-mode automations that the Home Assistant config API cannot delete, instead of silently reporting success when Home Assistant returns a 404.

## 0.1.4

- Route cloud relay Socket.IO traffic through `/backend-api/socket.io` by default so the add-on matches TerraMatrix test/prod nginx routing.

## 0.1.3

- Run the internal bridge service on port 3000 so nginx can own the Home Assistant ingress port 8099.

## 0.1.2

- Remove the runtime dependency on `bashio` from add-on service scripts.

## 0.1.1

- Disable Docker init for the add-on container so s6-overlay can run as PID 1.

## 0.1.0

- Initial release
- HA entity discovery and real-time state streaming
- Dashboard viewer with TerraMatrix component rendering
- Auto-generated dashboards based on discovered entities
- HA device control (lights, climate, covers, locks, media, switches)
- Cloud bridge for TerraMatrix AI and workflow integration
- Standalone mode for local-only operation
- Automation management (view, create, toggle HA automations)
- Entity history charts
