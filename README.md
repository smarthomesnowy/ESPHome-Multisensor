# ESPHome-Multisensor
<p>This is a new "Multisensor" that sits on my bookshelf next to my workstation.</p>
<p>It is based on a Wemos D1 mini ESP8266 board.</p>
<p>It has a PIR motion sensor, a DHT22 temprature/humidity sensor, an infra red reciever and an infra red transmitter</p>
<p>The motion sensor tracks motion across one side of my living room, the temprature sensor feeds into Home Assistant and works with the climate integration to turn on AC.</p>
<p>I used the infra red receiver to capture all of the codes of my existing infra red remote controls and then created buttons that appear on my Home Assistant dashboard. I then use an automation to turn on the TV then select the right HDMI source and set a volume level.</p>
