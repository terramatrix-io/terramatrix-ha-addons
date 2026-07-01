# Changelog

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
