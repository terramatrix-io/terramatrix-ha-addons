# TerraMatrix for Home Assistant

Runs the TerraMatrix edge runtime next to Home Assistant. It connects your Home
Assistant to TerraMatrix so you can see and control your home, and edit
automations, from TerraMatrix.

## Setup

1. In TerraMatrix, open **Settings → Integrations → Home Assistant** and click
   **Register bridge** (or **New token** on an existing instance). Copy the
   node ID and enrollment token it shows — the token is shown once.
2. In this add-on's **Configuration** tab, set:
   - `node_id` — the `TM_NODE_ID` value
   - `enrollment_token` — the `TM_ENROLLMENT_TOKEN` value
   - `cloud_url` — the TerraMatrix workflow service, for example `http://10.10.10.13:8001`
3. Start the add-on. Within a few seconds the instance shows **Online** in TerraMatrix.

The add-on talks to this Home Assistant directly; no Home Assistant token is needed.

## Configuration

| Option | Description | Default |
|--------|-------------|---------|
| `node_id` | Node ID from TerraMatrix | (empty) |
| `enrollment_token` | Enrollment token from TerraMatrix | (empty) |
| `cloud_url` | TerraMatrix workflow service URL | (empty) |
| `cloud_socket_path` | Socket.IO path on the cloud URL | `/socket.io` |
| `ha_url` | Only when Home Assistant runs on another machine | (empty) |
| `ha_token` | Long-lived token for `ha_url` | (empty) |
| `log_level` | Logging verbosity | `info` |

## Replacing a token

Click **New token** in TerraMatrix, paste the new enrollment token here and
restart the add-on. The old token stops working immediately. **Disconnect** in
TerraMatrix revokes the token without deleting anything.

## Support

- [GitHub Issues](https://github.com/terramatrix-io/terramatrix-ha-addons/issues)
