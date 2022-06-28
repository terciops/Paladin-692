# Paladin-693
This will contain the latest firmware for Paladin-6 (currently V693)
Suitable for all Sept 2020 daughterboard units fitted with a top temperature control switch.

Paladin 650 - 691 Changes

Better main loop math to smooth grid readings and accuracy.
Improved SSR work cycle calculation for smoother operation.
Revised 'Throttle' display improving linear response
Changes to DIP settings to accommodate full 'plug and play' RF433 operation.  Control still on Top switch - negating Temperature Control when fitted.
Implementation of internal, real time 'tuning' feature.  Requires a high accuracy grid reference to use / change values.  There are other ways, but more on that later and as required.
The bulk of the variation between Paladin Tuning values is in the motherboard.
Tuning value stored in EEPROM, valid for that motherboard Arduino pair.  Default 0.0630 = V650 equivalent.
2.5mm wiring and heavier duty connections to SSR.
RS232 and LoRa ESP32 interfaces now fully operational.  Auto detect for both on start up.
Temperature probe connector now a 3 pin keyed plug to a socket mounted on the motherboard.  Much easier to use.


Paladin 692/3 Changes

All RF433 operation now exclusively on the (added with RF433) Bottom Switch.  The top switch is exclusively Temp Control. DIP3-1 activates RF433.
Improved 'Throttle' graphic sensitivity to remove throttle display at low SSR work cycles.
Active temperature probe detection and recovery after 'SENSOR' fault.  Reboot no longer required once probe reconnected.
NO TEMP operation for underfloor heating etc no longer needs any special action.  Just leave off the Temperature probe.
Under latest Building code, Legionella protection can now be achieved by 60C+ for a minimum 1 hour every 7 days.

https://www.health.govt.nz/system/files/documents/publications/prevention-of-legionellosis-in-new-zealand-jul19.pdf

To achieve this without the considerable complexity of a timer using 62C as the Legionella and boost value to reset the Legionella clock flag.  (now set to 168 hours v 72 hours)
Overnight boosts (now to 62C - to mirror the Legionella requirement) and the Legionella boosts are now triggered at the overnight reset point.   This ensures that any top-up usage is shown the following morning.
The overnight reset point calculations have been reworked to be more reliably in the 10pm-4am range throughout the seasons.  Poor solar production will still attempt to thwart this, but hopefully less often.
The sensitivity of the 'Throttle Bar' has been reduced to dampen response at lower levels of diversion.  The throttle bar will only appear at approximately 900W+ of diversion activity.  The nett result is a smoother, less distracting display element.
