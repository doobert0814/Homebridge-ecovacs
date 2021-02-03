# Homebridge-ecovacs

Plugin for controlling your [deebot Ecovacs](https://www.ecovacs.com/global/deebot-robotic-vacuum-cleaner) from [Ecovacs](https://www.ecovacs.com/global/support/) through [HomeBridge](https://github.com/nfarina/homebridge) .

Each Deebot is shown through

- One fan. Fan speed will determine the deebot speed. Direction will handle auto / edge mode. Switching off will make the deebot stop, switching on will make it start cleaning,
- One Switch that will allow you to start lceaning (auto / edge mode depending on Fan direction), and go back to charge when switched off,
- One Switch that will play a sound on your Deebot,
- One Motion sensor that will be triggered in case your deebot needs attention.

The battery percentage / charging status is shown in the detail pane of each service.

`npm install -g homebridge-ecovacs`

## Homebridge configuration

Config as below:

```json
"platforms": [
  {
    "platform": "DeebotEcovacs",
    "email": "toto@kansas.com",
    "password": "toto",
    "countryCode" : "FR"
  }
]
```

Fields:

- `platform` must be "DeebotEcovacs" (required).
- `email` email used for your ecovacs account (required).
- `password` password of your ecovacs account (required).
- `country code` : country code for your account , value in : CH, TW, MY, JP, SG, TH, HK, IN, KR,US,FR, ES, UK, NO, MX, DE, PT, CH, AU, IT, NL, SE, BE, DK, OTHER (required).
- `refreshTimer` Optional - enable refresh of deebot state every X seconds, for automation purpose if you need to activate something else based on its state change (defaults : disable, accepted range : 30-600s).
- `cleanCache` Set it to true in case you want to remove the cached accessory (only those from this plugin). You have to restart homebridge after applying the option. Remove it after restart, otherwise it will be recreated at each startup.
- `deebotNames` Array of NickNames of the deebot to publish. Defaults to all found on your account.
- `publishBipSwitch` Optional - defaults to true - Publish the switch that makes the deebot beeps
- `publishFan` Optional - defaults to true - Publish the fan that makes speed cleaning available
- `publishSwitch` Optional - defaults to true - Publish the switch that makes on/off available
- `publishMotionDetector` Optional - defaults to true - Publish the motion detector to be triggered in case of hep needed by your deebot
- `publishAutoSwitch` Optional - Publish a switch to start in auto Mode.
- `publishEdgeSwitch` Optional - Publish a switch to start in edge Mode.
- `publishSpotSwitch` Optional - Publish a switch to start in spot Mode.
- `publishSpotAreaSwitches` Optional - Publish switches to start for each spot Area. Must be something like ["1","1,2"] or ["deebotName|1","deebotName2|1,2"] if you have multiple deebots
- `publishCustomAreaSwitches` Optional - Publish switches to start for each Custom Area. Must be something like ["(x1,y1,x2,y2)","(x1,y1,x2,y2)"] or ["deebotName|(x1,y1,x2,y2)","deebotName2|(x1,y1,x2,y2)"] if you have multiple deebots

See : https://github.com/mrbungle64/ecovacs-deebot.js/wiki/Clean-modes

## Inspiration

Many thanks to :

- [wpietri] for sucks python api and protocol
- [mrbungle64] for nice js port and revamp of sucks.js package
- every tester / contributor that test, and give feedback in any way !

[wpietri]: https://github.com/wpietri/sucks
[mrbungle64]: https://github.com/mrbungle64/ecovacs-deebot.js

