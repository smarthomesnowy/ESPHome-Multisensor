# ESPHome-Multisensor



## Idea

This is a new "Multisensor" that sits on my bookshelf next to my workstation.

It is based on a Wemos D1 mini ESP8266 board.
It has a PIR motion sensor, a DHT22 temprature/humidity sensor, an infra red reciever and an infra red transmitter
The motion sensor tracks motion across one side of my living room, the temprature sensor feeds into Home Assistant and works with the climate integration to turn on AC.
I used the infra red receiver to capture all of the codes of my existing infra red remote controls and then created buttons that appear on my Home Assistant dashboard. I then use an automation to turn on the [smart fireplace](https://github.com/smarthomesnowy/Smart-Fireplace) TV then select the right HDMI source and set a volume level.


## Parts used

- Wemos D1 mini ESP8266
- DHT22 temprature/humidity
- PIR motion sensor X2
- Infrared receiver
- Infrared transmitter


## Coding

### ESPHome
The hardest part of the coding for this device was first decoding the IR signals from the TV remote with the IR receiver then creating buttons in ESPHome to trigger the transmitter component to send the code to the TV.

```yaml
button:
  - platform: template
    name: "TV Turn Off"
    on_press:
      remote_transmitter.transmit_rc5:
        address: 0x00
        command: 0x0C

  - platform: template
    name: "TV Mute"
    on_press:
      remote_transmitter.transmit_rc5:
        address: 0x00
        command: 0x0D

  - platform: template
    name: "TV Volume Up"
    on_press:
      remote_transmitter.transmit_rc5:
        address: 0x00
        command: 0x15
        repeat:
         times: 2
         wait_time: 50ms

  - platform: template
    name: "TV Volume Down"
    on_press:
      remote_transmitter.transmit_rc5:
        address: 0x00
        command: 0x14

  - platform: template
    name: "TV Volume OK"
    on_press:
      remote_transmitter.transmit_rc5:
        address: 0x00
        command: 0x26
```

### Home Assistant
In Home Assistant I made some buttons on the dashboard for the ESPHome buttons so I can control the TV from the dashboard.

## Construction
Fitting all the components inside the small case I ordered was a challenge and the PIR sensors were just too large so I had to glue them on underneath the case.


## Pictures / Video
some images

## Conclusion
The device sits upside down under a shelf and has enough range to easily control the [smart fireplace](https://github.com/smarthomesnowy/Smart-Fireplace) TV and the motion sensors work great in covering the living room and hallway.
Cost of the device was about 20 euro including the sensors and the case, I think in the future a better idea would be to 3D print a better case.
