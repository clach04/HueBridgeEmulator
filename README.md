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

  * Python 2 only

Edit config file to change fake devices.
Edit config file to add/remove users to whitelist.

## Running

Uses Python stdlib, can either listen on port 80 (which under Unix platforms is a restricted port):

    python2 HueBridgeEmulator.py
    python HueBridgeEmulator.py

or override for non-default, e.g.:

    env HUE_PORT=1999 python HueBridgeEmulator.py

### Discovery

Works with https://github.com/clach04/discoverhue/blob/mybranch/mydemo.py

NOTE if another process is already listening on port 1900, will see errors on startup:

    error: [Errno 98] Address already in use

So (msearch) discovery will not work but light requests will work fine.

Does not work with https://github.com/ekux44/LampShade (which appears to work with Home Assistant), either on port 80 or something else.

### cURL Philips Hue samples

    echo IP needs to include colon port if NOT using port 80
    export USERNAME=nouser
    export IP=127.0.0.1:80
    export LIGHTNUM=1  # pick the first one
    curl -v http://${IP}/description.xml
    curl -v http://${IP}/api/${USERNAME}/lights
    curl -v http://${IP}/api/${USERNAME}/config

    curl -v http://${IP}/api/${USERNAME}/lights/${LIGHTNUM}
    curl -s -H "Accept: application/json" -X PUT --data "{\"on\": true}"  http://${IP}/api/${USERNAME}/lights/${LIGHTNUM}/state
    curl -s -H "Accept: application/json" -X PUT --data "{\"on\": false}" http://${IP}/api/${USERNAME}/lights/${LIGHTNUM}/state


