# OpenDTU Screenshots
Here are some unsorted screenshots as example.

---

You need to install the REST integration, which should look like this:
![REST Integration](./opendtu_rest_integation.JPG)

---

Some visualisation added:

Btw: You could see, that my 3rd panel is not fully exposed to the sun, it is "shaded" and produces less Watt than possible.
This shows me, that I should move the panel to another position (without shade).

![REST Integration](./opendtu_visualisation_example.JPG)

---

The direct call (without Home Assistant) to your OpenDTU should show something like this:

Btw: The "limit_relative" shown here is 88%, which ist 264 Watt.
In germany you are allowed 800 Watt at all, so 3*264=792 is below 800 Watt.
You could set this limit using OpenDTU, but I did not include this into the integration currently.

![REST Integration](./opend_dtu_rest_example.JPG)
