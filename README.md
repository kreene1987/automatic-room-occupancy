# automatic-room-occupancy
Automatic Home Occupancy Home Assistant Blueprint

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fkreene1987%2Fautomatic-room-occupancy%2Fblob%2Fmain%2Fautomatic-room-occupancy.yaml)

Code based on @gdeboos great start as he has indicated he is having health issues and cannot maintain. https://community.home-assistant.io/t/please-remove/258334

**Automatic Home Occupancy Home Assistant Blueprint**

Automatically turn on and off an occupancy input_boolean helper entity for a single room based on activity or non-activity (with timeout).

------SETUP------

The following helper entities are required:
- input_boolean.[room]_occupancy (input_boolean that will be turned on/off with occupancy)

The following entities are optional for full automation functionality:
- group.household (A grouped set of people in your house. Logic to turn on occupancy will only run if state is "home"".)
- input_boolean.[room]_occupancy_disabled (input_boolean that disables the automation)
- input_boolean.guest (input_boolean that will enable the automation when household is away)

------LOGIC------

Occupied triggered when ANY of the following conditions are met (all are optional).
- door binary_sensor (or group) state to "off"/closed (for interior rooms eg. bathrooms) 
- media player(s) state as specified (default: "playing")
- motion binary_sensor (or group) state to "on"
- room presence sensor (eg. room-assistant) state as specified

Occupancy is cleared when ALL of the following conditions are met (all are optional):
- door binary_sensor (or group) state to "on"/open for specified time (default: 0 mins)
- any media player state to state as specified (default: "playing")
- any motion binary_sensor (or group) state to "off" for specified time (default: 10 mins)
- presence sensor(s) all detected in different room or "not_home"

------OPTIONAL HELPERS------

Uses the following helpers to allow for front end control of timeouts. All default to 10 minutes if not provided.
- input_number.door_occupancy_timeout (in minutes, default: 0)
- input_number.media_occupancy_timeout (in minutes, default: 10)
- input_number.motion_occupancy_timeout (in minutes, default: 10)
- input_number.bluetooth_occupancy_timeout (NOT IN USE YET)
