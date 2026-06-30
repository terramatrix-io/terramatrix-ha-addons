# TerraMatrix for Home Assistant

AI-powered dashboards and intelligent automation for your Home Assistant instance.

## Quick Start

1. Add this repository to your Home Assistant add-on store
2. Install the TerraMatrix add-on
3. Start the add-on — it will automatically discover your HA entities
4. Open TerraMatrix from the sidebar to see your auto-generated dashboards

## Features

- **Auto-generated dashboards** based on your HA areas and devices
- **Real-time entity state** with live updates
- **Device control** for lights, climate, covers, locks, media players, and switches
- **Entity history charts** for sensors and other numeric entities
- **AI-powered automation** creation via natural language (requires TerraMatrix Cloud)
- **Custom dashboards** designed in the TerraMatrix web editor
- **Standalone mode** works without cloud connection

## Configuration

| Option | Description | Default |
|--------|-------------|---------|
| `cloud_url` | TerraMatrix cloud server URL | `https://app.terramatrix.io` |
| `cloud_token` | Authentication token for cloud features | (empty) |
| `log_level` | Logging verbosity | `info` |
| `standalone_mode` | Run without cloud connection | `false` |

## Cloud Connection (Optional)

To enable AI automation generation and cloud-designed dashboards:

1. Create an account at [app.terramatrix.io](https://app.terramatrix.io)
2. Register your HA instance in the TerraMatrix dashboard
3. Copy the cloud token into the add-on configuration
4. Restart the add-on

## Support

- [Documentation](https://docs.terramatrix.io)
- [GitHub Issues](https://github.com/terramatrix-io/terramatrix-ha-addons/issues)
