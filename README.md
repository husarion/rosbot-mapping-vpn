# rosbot-mapping-vpn

> :warning: **This repo is deprecated**. Use [rosbot-mapping](https://github.com/husarion/rosbot-mapping) instead.

Create a map of the unknow environment with ROSbot controlled over the Internet

## Quick Start

ROSbot and your laptop need to be in the same Husarnet network. 

## PC

Connect a gamepad to USB port of your PC/laptop. 

Then create `.env` file 

```bash
cp .env.template .env
```

check you LIDAR configs:

```
LIDAR_BAUDRATE=256000
LIDAR_SERIAL=/dev/ttyUSB0
```

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

> **Firmware version**
>
> Before running the project, make sure you have the correct version of a firmware flashed on your robot.
>
> Firmware flashing command (run in the ROSbot's terminal)
>
> ```
> docker stop rosbot microros || true && docker run \
> --rm -it --privileged \
> husarion/rosbot:humble-22-11-25 \
> /flash-firmware.py /root/firmware.bin
> ```

In the ROSbot's shell execute (in `/home/husarion/rosbot-mapping-vpn` directory)

```bash
docker compose -f compose.rosbot.yaml up
```