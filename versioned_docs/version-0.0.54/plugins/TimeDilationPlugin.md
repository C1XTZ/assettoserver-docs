---
description: Dynamically adjust the time multiplier based on the sun position
---

# TimeDilationPlugin

Plugin to dynamically adjust the time multiplier based on the sun position. It can be used to make time pass faster during daytime and slower during nighttime for example.

:::note

Longitude and latitude of the track are required in the `data_tracks_params.ini`

:::

## Configuration
Enable the plugin in `extra_cfg.yml`
```yaml
EnablePlugins:
- TimeDilationPlugin
```

Example configuration (add to bottom of `extra_cfg.yml`)
```yaml
---
!TimeDilationConfiguration
# Table to map sun angles to time multipliers. SunAngle is the altitude of the sun in degrees. 90° = sun directly overhead, -90° = sun directly underneath.
# Example config for 4x during the night, then slowly accelerating to 8x after sunrise, and then slowing down again to 4x shortly before sunset
LookupTable:
  - { SunAngle: 6, TimeMult: 4 }
  - { SunAngle: 12, TimeMult: 8 }
```