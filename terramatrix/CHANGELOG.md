# Changelog

## 2.1.3

- Whole-house Home/Away on wall tablets: the dial's − and + move every
  thermostat in the house together, including a heat/cool unit's range (both
  ends in one change, each inside the thermostat's own limits).
- The add-on now checks a thermostat is still in the mode a tablet's control
  was made for before changing it, so a Home or Away press never switches a
  thermostat between heat and cool, or puts a heat set-point into a cool one.
- Tells TerraMatrix it understands these newer tablet controls; older add-ons
  keep getting the controls they already support.
- A tablet may make up to 60 changes a minute (was 20), so one whole-house
  change reaches every thermostat; each device still changes at most once a second.
- A device removed or disabled in Home Assistant now disappears from the
  add-on straight away, instead of showing its last state.

## 2.1.2

- Wall tablets can run Home and Away thermostat controls: the add-on
  applies an Away range edit with both ends of the heat/cool range, checks the
  thermostat supports presets and ranges, and keeps a device's own correction.
- Thermostat mode pickers on a tablet are accepted.

## 2.1.1

- The add-on's own health check no longer goes through the panel, which
  (since 2.1.0) admits only Home Assistant's ingress. Home Assistant no longer
  shows the add-on as unhealthy.

## 2.1.0

- Wall-tablet kiosks (off unless `kiosk_enabled` is turned on). A paired
  tablet shows the pages and buttons your organization granted it and keeps
  working when the internet is down. It talks only to this add-on, on its own
  port (8443), and tablets can find the add-on on your network (8444/udp).
- The add-on now uses the host network, so tablets can find it by broadcast.
- Run as a plain container on a host network (outside Home Assistant), set
  `TM_PANEL_ALLOW` (for example `127.0.0.1`) so only those addresses can open
  the local panel.
  Its internal interface listens only inside the add-on, and the web panel is
  reachable only through Home Assistant, as before.
- Adds about 8–12 MB of memory at most when kiosks are on (pages are kept on
  disk, not in memory); nothing when they are off.

## 2.0.4

- Finishes the 2.0.3 fix. The stores were not only uncompacted but full: up to
  50,000 queued events and 500,000 history points, more than the add-on's
  memory can load. The bounds are now 5,000 queued events and 50,000 history
  points, and an oversized store is trimmed to its newest entries before it
  loads. Dropped entries are counted, as before.

## 2.0.3

- The add-on no longer restarts every 30 seconds on a busy Home Assistant. Its
  local stores only shrink when they are compacted, and a store that had grown
  too large made the add-on run out of memory while loading it — before the
  first compaction could run. Large stores are now compacted before they load.

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
