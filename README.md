# bluSensor® MQTT API

## Broker
You can use our **shared MQTT broker** free of charge. If your project requires a **dedicated and private MQTT broker** or if you want to use your **own broker**, you can use our **app** (bluSensor® AIR) to configure your sensors to connect to it. Using **TLS** and **client certificates** (stored on the sensor) is also already supported! Please contact us for details!

```
broker.blusensor.com
```

**Available Ports**

* 7883 (client)
* 7885 (websockets)
* 8883 (client,TLS)
* 8885 (websockets,TLS)

## Dashboard

We've implemented a basic dashboard to display current sensor values: https://broker.blusensor.com

<img src="screenshot_dashboard.png" width="800">

## MQTT Topics

```
iot/blusensor/v1/things/<SERIALNR>/telemetry
```

* **SERIALNR** = world-wide unique sensor serialnumber (18 characters)


Example:
```
iot/blusensor/v1/things/B01080112233445566
```

## MQTT Sensor Data (json)

#### Basic Sensor Information

```
{
  
  "serialnr" : "B01080112233445566",
  "name" : “bluSensor, Infinite Loop, Cupertino, CA 95014", 
  "location" : "bluSensor Lab Room 1"
  "type" : 1,
  "lat" : "37.7858340“
  "lon" : "-122.4064170",
  "ts_unix" : "1561698704",
  "ts_iso" : "2016-12-12 17:00:18.410",

  <sensor specific information>

}
```

* **serialnr**: sensor serialnumber
* **name**: user defined sensor name 
* **location**: user defined sensor location
* **type**: sensor type 
* **lat**, **lon**: GPS coordinates 
* **ts_unix**: UNIX timestamp of measurement (UTC)
* **ts_iso**: ISO8601 formatted timestamp of measurement (UTC)


#### Device Types

device type  | description             
------------ | -------------           
01           | Humidity & Temperature  
02           | Accelerometer           
03           | 3D Fusion (Euler)       
04           | Air Flow                
05           | Ambient Light           
06           | Accelerometer, Magnetometer, Gyroscope 
07           | (reserved)
08           | (reserved)
09           | (reserved)
10           | Air Quality 
11           | Usage Counter  
12           | (reserved)
13           | Temperature
14           | Infrared Array Camera  
15           | Particulate Matter 
16           | Proximity Distance 
17           | Proximity Counter
18           | People



### Sensor Specific Information

```
{
  <basic information>

  "hum" : 36.57,
  "tem" : 22.01,
  "dew" : 17.60, 
  "tvoc" : 550,
  "co2" : 1023,
}
```

sensor value            | json
------------            | -------------   
Humidity                | hum
Temperature             | tem
Temperature Probe       | tem_probe
Dewpoint                | dew
Particulate Matter      | pm1, pm2, pm4, pm10
CO2                     | co2
TVOC                    | tvoc
Air Flow                | airflow
Shake-It                | shakes_total, shakes_current
Acceleration            | acc_x / acc_y / acc_z
Gyroscope               | gyr_x / gyr_y / gyr_z
Magnetometer            | mag_x / mag_y / mag_z
3D (Euler Coordinates)  | euler_x / euler_y /euler_z
Usage Index             | uix
Light                   | light
Noise                   | noise
AIQ Index               | aiq_index, aiq_info
Pressure                | pressure
Infrared Array          | ir_cam
Distance                | distance
Distance Counter        | distance_count
People Presence         | people
People Counter          | people



## Development Tools

You can use any MQTT client to connect to our broker and subscribe to your sensor's data. 

We can recommend MQTT.fx!

#### MQTT.fx - Configuration (TLS)
<img src="screenshot_mqttfx_conf.jpg" width="800">

#### MQTT.fx - Sensor Data (JSON)
<img src="screenshot_mqttfx.jpg" width="800">

# Purchase Sensors

You can buy sensors and development kits on our website.
https://www.blusensor.com/en/products/wifi-sensors-internet-of-things/

Or you can also support us on Kickstarter!
https://www.kickstarter.com/projects/blusensor/blusensor-aiq-the-flexible-air-quality-monitor/

# Support

Having trouble with bluSensor® API or need development support? 

You will get direct support from our **core development team** (free of charge)!

You can contact us anytime at support@blusensor.com

You need a sensor type that is not listed yet?

Just drop us an email!
