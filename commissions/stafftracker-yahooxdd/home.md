---
title: Home
description: Thank you for ordering from me! This is the documentation for your order.
published: 1
date: 2024-11-28T17:07:56.257Z
tags: commissions-yahooxdd
editor: markdown
dateCreated: 2024-11-25T22:52:05.884Z
---

# **StaffTracker Plugin Configuration Documentation**

## **Overview**

The `StaffTracker` plugin is designed to log staff actions, including commands, chat messages, and punishments, to a Discord webhook. This helps track the activities of staff members in a Minecraft server, providing a detailed audit trail. Below is a breakdown of the configuration file and its options.

---

## **Configuration File Breakdown**

The configuration file allows you to customize which player actions should be tracked and where the logs are sent.

### **General Configuration**

- **debug** (boolean)  
  _Default: `false`_  
  This option enables detailed logging of every event into the console. This is useful for debugging and troubleshooting issues with the plugin. Set it to `false` to disable debug logs.

  ```yaml
  debug: false
  ```
- **webhook** (string)
	_Default: `"webhook"`_
  The URL of the Discord webhook where the logs will be sent. Replace this with your own Discord webhook URL.
  ```yaml
  webhook: https://discord.com/api/webhooks/your-webhook-url
  ```
- **players-to-track** (list of UUIDs)
  _Default: `Empty`_
  A list of player UUIDs whose actions will always be logged, regardless of the settings for other commands. You can add the UUIDs of the staff members you want to track.

  ```yaml
  players-to-track:
    - da7ac797-993a-46d1-b1c4-b26e0a038690
    - uuid2
    ```
### Command Tracking Configuration
- **all-commands** (boolean)
  _Default: `true`_
  When set to true, all commands executed by players will be logged to the webhook. When set to false, only the specific commands listed under commands and punish commands will be tracked.

  ```yaml
  all-commands: true
  ```
- **commands** (list of strings)
  Default: Empty
  A list of commands to be specifically tracked. When all-commands is set to false, only these commands will be logged. Example commands include /ban, /kick, /mute, and others.

  ```yaml
  commands:
    - /command
    - /anothercommand
    - /meow
    ```
### Punishment Command Logging
The plugin supports specific tracking for punishment commands such as /ban, /mute, /kick, /warn, and /msg. Each punishment command will be logged with additional details (e.g., player, time, and reason).

- **ban-command** (string)
  _Default: `/ban`_
  The command used to ban players. Change this if you use a custom command for banning.

  ```yaml
  ban-command: /ban
  ```
- **mute-command** (string)
  _Default: `/mute`_
  The command used to mute players. Change this if you use a custom command for muting.

  ```yaml
  mute-command: /mute
  ```

- **kick-command** (string)
  _Default: `/kick`_
  The command used to kick players. Change this if you use a custom command for kicking.

  ```yaml
  kick-command: /kick
  ```

- **warn-command** (string)
  _Default: `/warn`_
  The command used to warn players. Change this if you use a custom command for warnings.

  ```yaml
  warn-command: /warn
  ```
### Message Command Logging
- **message-command** (string)
  _Default: `/msg`_
  The command used to send private messages. Change this if you use a custom command for messaging.

  ```yaml
  message-command: /msg
	```
### Chat Logging
- **chat** (boolean)
  _Default: `true`_
  This option controls whether chat messages are logged. When set to true, all chat messages are logged. If set to false, only the players in the players-to-track list will have their chat messages logged.

  ```yaml
  chat: true
  ```

## Example Configuration
```yaml
# --------------------------------------------------------
# StaffTracker Configuration

# Useful Resources:
# * Arcane Discord: https://discord.gg/arcanestudios
# --------------------------------------------------------

# Debug
# This will log EVERY event into the console for easier debugging.
debug: false
#  
# Webhook URL
# This will be the URL for your webhook.
webhook: webhook
#  
# Staff list
# Use this list to determine which players will be logged.
players-to-track:
- uuid1
- uuid2
#  
# All commands
# Use this to toggle either: all commands to be logged OR the commands in the list below.
all-commands: true
#  
# Chat logging
# True: Log all chat
# False: Log chat from players in the list above
chat: true
#  
# Commands to track
# This is a general list of all commands that will be logged.
commands:
- /command
- /anothercommand
- /meow
#  
# Specific command logging
# This is where you will define your specific commands.
# Ban command
ban-command: /ban
# Mute
mute-command: /mute
# Kick
kick-command: /kick
# Warn
warn-command: /warn
# Message
message-command: /msg

# Author: 
# Joe Hosten 
# GitHub: https://github.com/joehosten
# Discord: @joehypews (462296411141177364)
```
## Additional Information
* Player UUIDs:
To track specific players, you can get their UUID from the server using /uuid <player_name>.

* Webhook Format:
The webhook will send messages to your Discord server in a readable format, detailing the command used, the player executing it, and any additional information like reason or time for punishments.

* Debugging:
Enabling the debug mode will print detailed logs to the console, making it easier to track and resolve issues with your configuration or plugin functionality.
## Contact and Support
* Author: Joe Hosten
* GitHub: https://github.com/joehosten
* Discord: @joehypews (462296411141177364)
* Arcane Discord: https://discord.gg/arcanestudios  

For any issues or questions, you can join the Arcane Discord or contact the author directly.