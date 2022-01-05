# beoported
Utility to use the Bang &amp; Olufsen Beoport PC2 on a Linux desktop

## Dependencies
On Debian systems one can run

```bash
apt install libboost-log-dev libboost-iostreams-dev libboost-thread-dev libboost-system-dev librabbitmq-dev libusb-1.0-0-dev libnotify-dev
```

## Build
```bash
mkdir build; cd build
cmake ..
make
```

## Usage

`./beoported [mode-char]`

Various mode characters have been used during development; 1 turns the device on, 0 turns it off.

'm' is main/monitor mode, which will listen for IR signal events and react appropriately.

Might need `sudo` priviliges to work.
