## HueBridgeEmulator

This is a fork of https://github.com/mariusmotea/HueBridgeEmulator

HueBridgeEmulator is a lite version of the DiyHue project that only runs with Python 2.
For more information about the more sophisticated DiyHue see:

  * https://github.com/mariusmotea/diyHue - older code line
  * https://github.com/diyhue/diyHue

Missing all functions that manage wifi lights and sensors. This is intended just to test Hue apps without a real Philips Hue Bridge, similar to:

  * https://github.com/SteveyO/Hue-Emulator
  * https://github.com/nooblucker/hueSimulator
  * https://github.com/armzilla/amazon-echo-ha-bridge

Useful for understand how bridge process rules. 
Edit config.json to add more lights or sensors.

Known to work with:

  * Android:
      * https://github.com/Domi04151309/HomeApp
      * https://www.hueessentials.com/

Known problems:

  * serves wrong content type for payloads (e.g. missing xml and json content type)
  * Python 2 only
