# automatic-room-occupancy
Automatic Home Occupancy Home Assistant Blueprint

Automatically turn on and off an ocupancy switch for a single room. 

------LOGIC------

Occupied when ANY of the following conditions are met (all are optional).   
	- door is shut   
	- any motoion  
	- any media player playing
	- door is shut (for rooms eg bathrooms)
	- on room presence (eg room-assistant)

Occupancy is clared under ALL of the following conditions being met (all are optional):
  - motion off for a set amount of time
  - no player in room played for a set amount of time   
  - no presence detected in room (TODO//: add a timer)
	
------HELPERS------

Uses the following helpers to allow for front end control of timeouts. All default to 10 minutes if not provided.
  - input_number.motion_occupancy_timeout
  - input_number.media_occupancy_timeout
  - input_number.bluetooth_occupancy_timeout(NOT IN USE YET)

------TODO------

- Use bluetooth timeout input (Help needed)
