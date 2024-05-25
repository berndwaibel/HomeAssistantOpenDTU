# OpenDTU and Shelly for photovoltaic systems - Integration into HomeAssistant

## Possible integrations
The integraton of the photovoltaic system is my first home automation project.
As I would like to know, how much energy will be delivered, I had a look at the following integrations:
Da ich auch wissen möchte, wie viel Strom ich erzeuge, habe ich folgende Integrationen mir angesehen:
1. Shelly Cloud
2. IOBroker
3. MQBroker or MQTT
4. Home Assistant

### Integration using Shelly devices and the Shelly Cloud
At first I bought a Shelly1PM and integrated it into the power connection.
The shelly device could be controlles with an handy app, which does a very good visualization of the data, 
also the controlling of the shelly devices is really easy (using the app or simply by using the homepage of the device.)

The app uses the (chinese) Shelly cloud, but the software in the Shelly device, and also the app is perfect.
Also, the long-running power summery in the app is a wonderful feature.
The Shelly device come with an open api, so you do not need to use the cloud.

At all, I like the shelly devices, and the software running on them, because they are open, well-designed and 
they are very flexible. The fact that the app is using the cloud is not a problem for me, as I use different clouds every day.
But as it is not necessary, I used the solution with home assistant.

Sometimes there seems to be a lag when using the app, cause the network connection from my phone to the cloud 
may not be always as stable as i which.
After all, I decided to integrate the Shelly device directly into Home Assistant.

### Integration using ioBroker
The integration using [ioBroker](https://www.iobroker.net/) seems more complex than Home Assistant,
and maybe more limited. As I also want to integrate more and more devices (like doorbells, cameras, etc.)
I deciced not to use ioBroker.
Maybe I will set up this on my NAS sometimes. 

### Integration using MQBroker or MQTT
The integration using [MQTT](https://mqtt.org/) seems also to be limited.
For visualization I need to setup Elastic and Grafana, which would be no problem, but is a little more effort,
even for long time storage of the metrics. I use grafana and ELK on work.
So I would like to do it, as it is interesting, but due to the effort I skipped this.
Maybe I will set up this on my NAS sometimes.

### Integration using Home Assistant
The integration using [Home Assistant](https://www.home-assistant.io/) seems to be the easiest way to solve the problem, and visualize the data
even for longer time periods. So I set up Home Assistant as virual machine on my PC first.
For Home Assistant there are a lot of integrations, so I decided to go on with this.
The way of work is described on the page [HOMEASSISTANT.md](./HOMEASSISTANT.md)
