##Introduction
This plugin offers Smartthings MQTT Bridge support, written for my collection of contact and motion sensors and offers configurable accessories.

Further information can be found here: https://github.com/stjohnjohnson/smartthings-mqtt-bridge
##Setup
````bash
npm install -g homebridge-smartthings-mqtt
````
###Configuration
By default the SmartthingsMQTT plugin will bind to the smartthings topic. This can be overridden by adding "topic": to the platform configuration. The general format is as follows:
````
smartthings/Patio Doors/state
````
Devices added to smartthings can be controlled through the bridge as well, if you use the appropriate characteristics and topics. For example to set the brightness of a bulb, the value will be sent to:
````
smartthings/Bulb Name/level
````
Or alternatively for a switch on or off is sent to:
````
smartthings/Fireplace Lights/switch'
````
Below is an example of how to configure the platform. As this gets developed further and my smartthings / homebridge and homekit automation system gets more complex, I will give examples on how to build custom services and characteristics.
````javascript
{
	...
	"platforms": [{
		"platform": "SmarthingsMQTT",
		// By default this will be bound to the smartthings topic, there is no need to specify it here.
		"topic": "smartthings",
		"accessories": [{
			"name": "Accessory Name",
			// defaults to accessory name
			"topic": "MQTT Accessory Topic HERE",
			"types": [{
				"type": "contact",
				"characteristics": [{
					"type": "state",
					// defaults to state
					"topic": "MQTT TOPIC HERE"
				}]
			}, {
				"type": "temperature",
				"characteristics": [{
					"type": "temperature"
					// defaults to temperature
					"topic": "MQTT TOPIC HERE"
				}]
			}]
		}]
	}]
}
````
###Notes:
* This is a work in progress based around my own needs and the devices I have!
* If you decide to use this and have issues, raise an issue in github issues.
* HAVE FUN!