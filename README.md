# ansible-macos-settings
Ansible role to manage personal settings in macOS.

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
  # Set standby delay in seconds, default = 3600, 24 hours = 86400, disabled = false
  standby_delay: 86400

  # Set system boot up chime volume
  boot_volume: false #"00%"

  # Remove duplicates in the “Open With” menu
  remove_duplicates: true

  # Restart automatically if the computer freezes
  restart_on_freeze: true

  # Never go into computer sleep mode
  sleep_delay: "Never"

  # Disable Notification Center and remove the menu bar icon
  notification_center: false

  # Disable local Time Machine snapshots
  local_timemachine: false

  # Set hibernate mode:
  # hibernatemode = 0 (binary 0000) by default on supported desktops. The system will not back memory up to
  #   persistent storage. The system must wake from the contents of memory; the system will lose context on
  #   power loss. This is, historically, plain old sleep.
  #
  # hibernatemode = 3 (binary 0011) by default on supported portables. The system will store a copy of mem-ory memory
  #   ory to persistent storage (the disk), and will power memory during sleep. The system will wake from
  #   memory, unless a power loss forces it to restore from disk image.
  #
  # hibernatemode = 25 (binary 0001 1001) is only settable via pmset. The system will store a copy of mem-ory memory
  #   ory to persistent storage (the disk), and will remove power to memory. The system will restore from
  #   disk image. If you want "hibernation" - slower sleeps, slower wakes, and better battery life, you
  #   should use this setting.
  hibernate_mode: 0

  # Remove the sleep image file to save disk space
  remove_sleepimage: false

  # Enable or disable sudden motion sensor (not userfull on SSD/Flash drives)
  sudden_motion_sensor: false

  # Set the timezone; see `systemsetup -listtimezones` for other values
  timezone: "Europe/Berlin"

  # Start/stop iTunes listening to the keyboard media keys
  itunes_media_keys: true

  # Show the ~/Library folder
  hide_library_folder: false

  # Enable the MacBook Air SuperDrive on any Mac
  superdrive: true

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
          standby_delay: 86400
          boot_volume: false
          remove_duplicates: true
          restart_on_freeze: true
          sleep_delay: "Never"
          notification_center: false
          local_timemachine: false
          hibernate_mode: 0
          remove_sleepimage: false
          sudden_motion_sensor: false
          timezone: "Europe/Berlin"
          itunes_media_keys: true
          hide_library_folder: false
          superdrive: true
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
              standby_delay: 86400,
              boot_volume: false,
              remove_duplicates: true,
              restart_on_freeze: true,
              sleep_delay: "Never",
              notification_center: false,
              local_timemachine: false,
              hibernate_mode: 0,
              remove_sleepimage: false,
              sudden_motion_sensor: false,
              timezone: "Europe/Berlin",
              itunes_media_keys: true,
              hide_library_folder: false,
              superdrive: true,
              spotlight_hide_tray_icon: false,
              spotlight_reindex: false
            }
          }
```
