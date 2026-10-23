# IoT SIM APN & SMS Setup Guide for GPS Trackers

APN setup by SMS command for common cellular GPS trackers, vehicle telematics units and dash cams using a [Quanqiu IoT](https://www.globallotsim.com) Global IoT SIM.

> **APN:** most Quanqiu IoT SIMs use the APN `mobile` with no username or password. Some plans use a different APN. Always use the APN printed on the delivery sheet that came with your SIMs. Command formats also vary by firmware version, so check your tracker's manual if a command is not accepted.

## Quick links
- Website: [globallotsim.com](https://www.globallotsim.com)
- Guide: [IoT SIM for GPS trackers and fleet dash cams](https://www.globallotsim.com/iot-sim-for-gps-trackers-and-fleet-dash-cams/)

---

## Before you start

1. Insert the SIM with the tracker powered off.
2. Make sure the SIM can receive SMS if you configure by SMS. Ask your account manager whether SMS is enabled on your plan.
3. Send the commands from a phone to the SIM's number (MSISDN).

## 1. Concox / Jimi (GT06N and similar)

```text
APN,mobile#        set the APN
SERVER,0,<your-server-domain-or-ip>,<port>,0#   point the tracker to your platform
PARAM#             read back the current settings
```

## 2. Teltonika (FMB / FMC series)

Teltonika SMS commands start with the SMS login and password, separated by spaces. With no login or password set, start the message with **two spaces**:

```text
  setparam 2001:mobile
  setparam 2002:
  setparam 2003:
  getparam 2001
```

`2001` is the APN, `2002` the APN username and `2003` the APN password.

## 3. Coban (TK103 and similar)

The default password is usually `123456`:

```text
apn123456 mobile
```

## Troubleshooting

| Symptom | Check |
|---------|-------|
| Tracker replies to SMS but never shows online | APN spelling; server address and port; data roaming enabled |
| No SMS reply | SMS enabled on the SIM; correct number; tracker powered and registered |
| Online, then offline after days | Data limit or SIM suspension; check usage in the connectivity management platform |

## Related tools and guides

- [IoT data usage calculator](https://www.globallotsim.com/iot-data-usage-calculator/) — estimate monthly data per device and per fleet ([source](https://github.com/loginzhou/iot-data-usage-calculator))
- [IoT SIM for GPS trackers: 30 MB plans, pooled data and APN setup](https://www.globallotsim.com/gps-tracker-sim/)

## License

MIT
