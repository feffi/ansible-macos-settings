# ansible-macos-settings
Ansible role to manage settings in macOS.

[![Build Status](https://img.shields.io/travis/feffi/ansible-macos-settings.svg)](https://travis-ci.org/feffi/ansible-macos-settings) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-macos-settings/total.svg)](https://github.com/feffi/ansible-macos-settings) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-macos-settings.svg?style=social&label=Fork)](https://github.com/feffi/ansible-macos-settings) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-macos-settings.svg?style=social&label=Star)](https://github.com/feffi/ansible-macos-settings) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-macos-settings.svg?style=social&label=Watch)](https://github.com/feffi/ansible-macos-settings) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-macos-settings/blob/master/LICENSE)

## Requirements
- Ansible 2.3

### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```yaml
- src: https://github.com/feffi/ansible-macos-settings.git
  name: feffi.macos-settings
```

## Role Variables
All role based variables are listed below, along with default values:

```yaml
macos_settings:
  # Set system boot up chime volume
  boot_volume: false #"00%"

  # Disable Notification Center and remove the menu bar icon
  notification_center: false

  # Enable or disable sudden motion sensor (not userfull on SSD/Flash drives)
  sudden_motion_sensor: false

  # Start/stop iTunes listening to the keyboard media keys
  itunes_media_keys: true

  # Hide Spotlight tray-icon (and subsequent helper)
  spotlight_hide_tray_icon: false

  # Rebuild the spotlight index from scratch
  spotlight_reindex: false
```

## Dependencies
None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        macos_settings:
          boot_volume: false
          notification_center: false
          sudden_motion_sensor: false
          itunes_media_keys: true
          spotlight_hide_tray_icon: false
          spotlight_reindex: false

      roles:
        - { role: feffi.macos-settings }
```
Or with local parameters:

```yaml
    - hosts: all
      roles:
        - { role: feffi.macos-settings,
            macos_settings: {
              boot_volume: false,
              notification_center: false,
              sudden_motion_sensor: false,
              itunes_media_keys: true,
              spotlight_hide_tray_icon: false,
              spotlight_reindex: false
            }
          }
```
