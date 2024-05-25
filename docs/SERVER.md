# OpenDTU and Shelly for photovoltaic systems - Integration into HomeAssistant

## Integration using a own server hardware and HomeAssistant
For running HomeAssistant you need to have a dedicated server. The following options are possible:
1. a Rasperry Device with external disk storage and power supply
2. a ThinClient als server
3. a Synology NAS (oder a QNap NAS) with support for virual machines.

### Rasperry
For using **Rasperry** I need to attach an external storage, and a power supply.
However, I would like to have a case for the device.
That seems to be possible, but to install this permanently would be time consuming. 
Using the Home Assistant Blue/Green/Yellow would be an option. But this seems to get more expensive than expected.

### Thin Clients
I thought about using a used **Thin Clients**, as this should be not to expensive.
They normally are not consuming much energy, as they have passive cooling. And it comes with a case. 
The hardware will run 24/7, so should not be energy consuming.
After some time searching the internet, I could not figure out which hardware would be useful for mee,
so I skipped this idea.

### NAS System
I decided to use a **Synology NAS**, because I would also need to setup a permanent data backup solution.
On work I used Synology before, so I decided to buy one. QNap would be fine, too.
Important for the usage for HomeAssistant is, that the NAS need to support virtual machines.

So I bought a DS224+. The "plus" is important, as the plus models could be extended with memory.
The included 2GB standard memory is completely used by the NAS itself, so it could not be used for any virtual machine.
So I extended it with 16 GByte more. There is a good video about, and I used exactly the RAM he recommeded.

See: Synology DS224+ RAM Upgrade by Daniel Medic: https://www.youtube.com/watch?v=PdeafJfMXdw

The installation of the virtual maschine for Home Assistant is described on the website from Home Assistant,
and I just followed exactly the steps described there. For the Synology I used the "HAOS" on "other systems",
and loaded the OVA file. See https://www.home-assistant.io/installation/alternative
