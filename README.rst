pe32me162irpy_pub
=================

**Project Energy 32:** *Read electricity meter (ISKRA ME162), through
optical port, export power usage to MQTT.*

This project contains *Python* code to read values from the
*ISKRA ME-162 electricity meter* and push them to an *MQTT broker*.

(This is the *Python* version of `pe32me162ir_pub
<https://github.com/wdoekes/pe32me162ir_pub>`_ -- a version in *C* that runs
on an *ESP8622*.)

Features:

- Although the *ISKA ME162* does not include power readouts (in Watt), we
  query the total energy consumed/produced (in Watt-hour) every second
  or so. This allows us to get a fair estimate of instantanous power
  usage. This can in fact give a better estimate than just sampling
  instantaneous power every now and then (which would be possible on other
  meters).

Required hardware: a so-called optical probe.

- *2023* - Bret McGee offers pre-soldered *optical probes* at `ebay UK
  <https://www.ebay.co.uk/itm/204371156344>`_. You'll likely want to 3D
  print a `plastic cover <https://www.thingiverse.com/thing:2652216>`_
  with magnets for easy attachment to your meter.

  *(I've been told Aalborg hackers stopped shipping their packages:
  "Bemærk: Vi sælger ikke længere kits.")*

- *2021* - On the `Hal9k Kamstrup Project page
  <https://wiki.hal9k.dk/projects/kamstrup>`_ (by Aalborg hackers) you can
  find instructions to build an *optical probe* (infrared transceiver) to
  communicate with *Kamstrup electricity meters* using the optical
  communications port. Such an optical communication port is available on
  several other electricity meters, like the *ISKRA ME-162* commonly found
  in the Netherlands. This optical probe can also be used on those.

For details on infrared (IR) interfacing with the electricity meter,
using the *IEC62056-21* protocol, I recommend browsing the `pe32me162ir_pub
<https://github.com/wdoekes/pe32me162ir_pub>`_ source code.

See also `pe32powerpy_pub <https://github.com/wdoekes/pe32powerpy_pub>`_
where this project is included along with code to read Solar Panel
output. The combined values allow for plotting near-realtime usage
graphs.


----
TODO
----

- Compare/try https://github.com/pwitab/iec62056-21
- Document raspberry PI setup somewhere..

----

*Project energy 32* is a suite of personal home readout/automation
tools. Batteries are *not* included. You need to set up an *MQTT
broker*, a database to store the readouts, a backend that subscribes and
inserts the values, vacuuming/pruning code, and something to display the
values (like *Grafana*).
