# OpenDTU and Shelly for photovoltaic systems - Integration into HomeAssistant

## Integration using own hardware and HomeAssistant
So I decide to user Home Assistant. For running Home Assistant you need to have a self hosted server. 
For hardware I decided to us a Synology NAS, details are described here: [SERVER.md](./SERVER.md).

## Integration of the devices into HomeAssistant

At least I need to integrate to devices into Home Assistant:
1. Shelly 1PM
2. OpenDTU

Both devices could measure the energy, which is produced by the photovoltaic systems. So they do the same, and
one would be enough. But the OpenDTU could also be used to configure the Hoymiles inverters.
It costs about 40 Euro, but the DTU from Hoymiles is about 100 Euro.
As I would not like to have a bad looking case, I bought the OpenDTU pre-configured including a case.
See here for details: https://shop.blinkyparts.com/de/OpenDTU-NRF-Deine-Auswertung-fuer-deine-Balkonsolaranlage-kompatibel-zu-Hoymiles-HM-Serie-NRF-Modul/blink237542

### Integration of the Shelly devices into HomeAssistant
**Shelly** could be easily integrated into Home Assistant, including discovery.
As there is not much to do, I do not describe the work I did for this.

### Integration of the OpenDTU device into HomeAssistant
The **OpenDTU** device could not be easily integrated into Home Assistant, except via the MQTT protocol.
As I would not like to measure only the energy, but also want to show some static data about the device,
I decided to set up this project. The aim is to describe the concept and the solution, 
as there is limited context about this on the internet.

At first, I tried to find a "plugin" or "integration" for the OpenDTU into Home Assistant.
As I ordered und soldered the OpenDTU hardware for configure the inverters, I decided to integrate them.

There are the following possibilities to integrate the OpenDTU into Home Assistant.
1. Integration using MQTT
2. Integration using a scrapping of the GUI of the device (https://www.home-assistant.io/integrations/scrape/)
3. Integration using the REST API of the OpenDTU device
4. Integration using Prometheus of the OpenDTU device
5. Integration using a self written plugin or integration module.

The **Integration using MQTT** is good documented, so I will not describe it here.
But I think, that there is only a measurement of the energy. Not showing any static data about the device.
Generally the OpenDTU sends events via MQTT to the Home Assistant Server (push mode).

The **Scrapping of the GUI** is nothing I would like, as this is very depending on the GUI.
Also the GUI does only send calls to the REST API of the device, which I could ask directly.
So I decide not to use the scraping integration.

As the **REST API of the OpenDTU** is very well documented and very comprehensive, I decided to use this.
The API is not considered to be stable and could change in future releases without announcement, but this is okay.
The work I did is mainly to work through the API and find out how to configure the values in the REST Integration.
See here for the API: * OpenDTU Web API: https://www.opendtu.solar/firmware/web_api/

### Integration of the OpenDTU device into HomeAssistant using REST API calls

The kind of integration i used, to integrate the device into Home Assistant, is via the flexible REST Module described
here: https://www.home-assistant.io/integrations/rest/ and here: https://www.home-assistant.io/integrations/sensor#device-class

So to integrate the device you only need to write a YAML file, not using any programming language (as python).
For me this is good, and the yaml file is described under the "src" folder.
The REST API is called every 60 seconds, so in contrast to MQTT this is a pull mode.

There are some limits using this YAML file and the REST API:
* The REST API is fixed when using the sensor, so each inverter (in my case 3) need to be listed in the file.
* There is no discovery and no dynamic listing of inverters
* I do not use the "push" methods, as they require authentication (and I do not need these methods)

### Integration of the OpenDTU device into HomeAssistant using Prometheus
I discovered, that one of the REST APIs of OpenDTU is delivering Prometheus data.
Maybe this could also be a way to integrate the data into Home Assistant.

### Integration of the OpenDTU device into HomeAssistant using a new plugin
The best way would be to have a **Integration using a new plugin**, but this would need to dive deeper into HAOS.
Maybe I will try this.

A plugin would be extend the possibilities:
1. Dynamic discovery of inverters and modules.
2. Templates for visualization
3. Controlling of the OpenDTU (instead configuring POST requests)
4. Configure the integration (e.g. User and Passwort)
5. Maybe mix the pull (REST API) and the push (MQTT) mode parallel.
6. Discovery of OpenDTU devices inside the network
7. ...

### Further work
Maybe a mix of MQTT (push), REST API (pull) and Prometheus would be good.
Also, I would like to write a plugin, but I am not sure if I could find time doing that.

