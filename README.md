# ha-processes
Collection of processes I need for running and maintaining home assistant.


# Configuration

## Images on the Pi

| Image | Container Name | Description |
| --- | --- | --- |
| koenkk/zigbee2mqtt | z2m2 | Enables Generic Zigbee functionality using the conbee 2 stick in the Pi over MQTT |
| esclipse-mosquitto | mqtt | MQTT Broker - port 1883 |
| portainer/portainer | ecstatic_goldwasser | Portainer - enables GUI management of docker conatiners, pretty useless except for stop/start/restart and deleting containers |
| ghcr.io/home-assistant/raspberrypi4-homeassistant:stable | homeassistant | Home assistant instance. Self explainatory |

## Device details

### Tags

* TYA : Tuya Based
* TP : TP-Link
* KS : Kasa
* ZB : Zigbee

* WL : White Light
* CL : RGB Colour Light
* RGB : RGB Strip / Controller
* PL : Plug Socket

### Device List

| Device | Tag | Location | IP | Details |
| --- | --- | --- | --- | --- |
| Tuya Landing Light | TYA-WL-A | Landing | 107 | |
| Tuya Dining Light | TYA-WL-B | Dining Room | 240 | |
| Valve Index | TYA-PL-A | Office | 6 | |
| Basestation 2 | TYA-PL-B | Dining Room | 240 | |
| Tapo L510 | TP-WL-A | Living Room | 74 (DHCP) | |
| Tapo L510 | TP-WL-B | Hallway | 177 (DHCP) | |
| Tapo L510 | TP-WL-C | Bedroom | 156 (DHCP) | Left |
| Tapo L510 | TP-WL-D | Bedroom | 121 (DHCP) | Right |
| Kasa KL130B | KS-CL-A | Living Room | 93 (DHCP) | |


# Docker Tasks

## Updating Home Assistant

From: https://community.home-assistant.io/t/updating-home-assistant-inside-docker/50428/2

Just need to stop, delete pull and run the image:

```
docker stop homeassistant
docker rm homeassistant
docker pull ghcr.io/home-assistant/raspberrypi4-homeassistant:stable
docker run -d --name homeassistant --privileged --restart=unless-stopped -e TZ=MY_TIME_ZONE -v /home/pi/ha:/config --network=host ghcr.io/home-assistant/raspberrypi4-homeassistant:stable
```

