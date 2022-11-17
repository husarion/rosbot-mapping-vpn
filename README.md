# rosbot-mapping-vpn

Create a map of the unknow environment with ROSbot controlled over the Internet

## Quick Start

ROSbot and your laptop need to be in the same Husarnet network. 

Connect a gamepad to USB port of your PC/laptop. 

Then create `.env` file 

```bash
cp .env.template .env
```

check you LIDAR configs and paste [Husarnet VPN](https://husarnet.com/docs/manual-client/) hostnames of your ROSbot and laptop

```
LIDAR_BAUDRATE=256000
LIDAR_SERIAL=/dev/ttyUSB0
DDS_PEER_1=husarnet-hostname-of-my-laptop
DDS_PEER_2=husarnet-hostname-of-my-rosbot

```

## PC

Sync workspace with ROSbot

```bash
./sync_with_rosbot.sh rosbotabc
```

and run Rviz with a gamepad controller on your PC:

```bash
xhost +local:docker && \
docker compose -f compose.pc.yaml up
```

## ROSbot

In the ROSbot's shell execute (in `/home/husarion/rosbot-mapping-vpn` directory)

```bash
docker compose -f compose.rosbot.yaml up
```