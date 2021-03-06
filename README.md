<p align="center">
  <a href="https://github.com/homebridge/verified/blob/master/verified-plugins.json"><img alt="Homebridge Verified" src="https://raw.githubusercontent.com/Brandawg93/homebridge-nest-cam/master/branding/Homebridge_x_Nest.svg?sanitize=true" width="500px"></a>
</p>

# homebridge-nest-cam

View your Nest cams in HomeKit using [Homebridge](https://github.com/nfarina/homebridge) with this plugin.

[![NPM](https://nodei.co/npm/homebridge-nest-cam.png?compact=true)](https://nodei.co/npm/homebridge-nest-cam/)

[![PayPal](https://img.shields.io/badge/paypal-donate-yellow?logo=paypal)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=CEYYGVB7ZZ764&item_name=homebridge-nest-cam&currency_code=USD&source=url)
[![BuyMeACoffee](https://img.shields.io/badge/coffee-donate-orange?logo=buy-me-a-coffee&logoColor=yellow)](https://www.buymeacoffee.com/L1FgZTD)

[![verified-by-homebridge](https://img.shields.io/badge/homebridge-verified-blueviolet?color=%23491F59)](https://github.com/homebridge/homebridge/wiki/Verified-Plugins)
![build](https://github.com/Brandawg93/homebridge-nest-cam/workflows/build/badge.svg)
[![Discord](https://camo.githubusercontent.com/7494d4da7060081501319a848bbba143cbf6101a/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3433323636333333303238313232363237303f636f6c6f723d373238454435266c6f676f3d646973636f7264266c6162656c3d646973636f7264)](https://discord.gg/pc2pqmh)
[![Downloads](https://img.shields.io/npm/dt/homebridge-nest-cam?logo=npm)](https://nodei.co/npm/homebridge-nest-cam/)

[![npm (tag)](https://img.shields.io/npm/v/homebridge-nest-cam/latest?logo=npm)](https://www.npmjs.com/package/homebridge-nest-cam/v/latest)
[![npm (tag)](https://img.shields.io/npm/v/homebridge-nest-cam/test?logo=npm)](https://www.npmjs.com/package/homebridge-nest-cam/v/test)
[![GitHub commits since latest release (by date)](https://img.shields.io/github/commits-since/brandawg93/homebridge-nest-cam/latest?logo=github)](https://github.com/Brandawg93/homebridge-nest-cam/releases/latest)

| [FAQ](https://github.com/Brandawg93/homebridge-nest-cam/wiki/FAQ) | [Troubleshooting](https://github.com/Brandawg93/homebridge-nest-cam/wiki/Troubleshooting) | [Error Codes](https://github.com/Brandawg93/homebridge-nest-cam/wiki/Error-Codes)
|---|---|---|

## Notes
- This plugin *does not* use the old access token authentication method as Google is urging users to [switch to Google accounts](https://www.macrumors.com/2020/05/05/nest-two-factor-authentication-from-may/).

## Installation
1. Install this plugin using: `npm install -g --unsafe-perm homebridge-nest-cam`
2. Add google authentication to `config.json`
3. Run [Homebridge](https://github.com/nfarina/homebridge)
4. Login with [homebridge-config-ui-x](https://www.npmjs.com/package/homebridge-config-ui-x) or use the [manual authentication method](https://github.com/Brandawg93/homebridge-nest-cam/wiki/Manual-Authentication).

### FFmpeg
By default, `libx264` is used as the h264 encoder. If you would like to use a hardware-accelerated encoder instead, refer to the [h264 Hardware Encoders Wiki](https://github.com/Brandawg93/homebridge-nest-cam/wiki/h264-Hardware-Encoders).

### Setting up the Config.json
#### googleAuth
Google Accounts are configured using the `"googleAuth"` object in `config.json`, which contains two fields, `"issueToken"` and `"cookies"`. An example is shown below. These fields will be generated automatically when using [homebridge-config-ui-x](https://www.npmjs.com/package/homebridge-config-ui-x), otherwise, they can be found in your Nest account using the [manual authentication method](https://github.com/Brandawg93/homebridge-nest-cam/wiki/Manual-Authentication).

```
{
    "platform": "Nest-cam",
    "ffmpegCodec": "libx264",
    "options": {
      "motionDetection": true,
      "streamingSwitch": true,
      "disableAudio": false
    },
    "googleAuth": {
        "issueToken": "https://accounts.google.com/o/oauth2/iframerpc?action=issueToken...",
        "cookies": "SMSV=ADHTe..."
    }
}
```

#### options
Extra options can be enabled/disabled depending on which switches and sensors you would like to see in the Home app. Here is the current list of available options:

| Name              | Description                                                         | Type             |
|-------------------|---------------------------------------------------------------------|------------------|
| streamQuality     | The quality of the stream from LOW to HIGH                          | number (1-3)     |
| alertCheckRate    | How often to check for alerts                                       | number (seconds) |
| alertCooldownRate | How long between consecutive alert notifications                    | number (seconds) |
| alertTypes        | What type of alerts to receive                                      | array            |
| importantOnly     | Only send notifications on events considered important              | boolean          |
| motionDetection   | Enable/disable the motion sensors                                   | boolean          |
| doorbellAlerts    | Enable/disable doorbell ring notifications                          | boolean          |
| doorbellSwitch    | Enable/disable doorbell automation switch                           | boolean          |
| streamingSwitch   | Enable/disable the ability to turn the camera on or off             | boolean          |
| chimeSwitch       | Enable/disable the ability to turn the doorbell chime on or off     | boolean          |
| audioSwitch       | Enable/disable the ability to turn the camera audio on or off       | boolean          |
| pathToFfmpeg      | Specify the path to a custom FFmpeg binary                          | string           |
| structures        | Specify the structure ID of which structures' cameras to see        | array            |

## Features
- View cameras within homekit.
- Receive notifications and set routines for motion or when the doorbell is rang.
- Receive notifications for specific motion events.
- Listen and talk back to people on equipped cameras.
- Enable/disable the indoor chime on Hello doorbells.

## Join the Discord
Unfortunately, there is no way for me to test every subscription, camera type, and feature. If you would like to help me test new features and enhancements, or if you have general questions or need support, join the official [Homebridge Discord Server](https://discord.gg/pc2pqmh).

## Credits
This plugin was originally developed by [KhaosT](https://github.com/KhaosT).

This plugin was converted to typescript using both [homebridge-ring](https://github.com/dgreif/ring) and [homebridge-examples](https://github.com/homebridge/homebridge-examples).

## Donate to Support homebridge-nest-cam
This plugin was made with you in mind. If you would like to show your appreciation for its continued development, please consider making [a small donation](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=CEYYGVB7ZZ764&item_name=homebridge-nest-cam&currency_code=USD&source=url).

## Disclaimer
This plugin and its contributers are not affiliated with Google LLC or Nest Labs in any way.
