# ansible-macos-settings
Ansible role to manage personal settings pictures in macOS.

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
  

```

## Dependencies
None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        macos_settings:
          
      roles:
        - { role: feffi.macos-settings }
```
Or with local parameters:

```yaml
    - hosts: all
      roles:
        - { role: feffi.macos-settings,
            macos_settings: {
              
            }
          }
```
