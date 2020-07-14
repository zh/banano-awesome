# How to setup bPoW on Raspberry Pi

> ([posted on Discord by happy_haVoc, July 13th, 2020](https://discordapp.com/channels/415935345075421194/626058996578648065/732576731952840807))

## Pre-requirements

Setup [Raspberry Pi OS ](https://www.raspberrypi.org/downloads/) (64 bit on **RPI 3B and higher**).


## Enable access

First on **Raspberry Pi** [enable SSH](https://www.raspberrypi.org/documentation/remote-access/ssh/). Then go to your Windows/Linux/OSX PC an **connect via SSH** to the Raspberry Pi machine.

## bPoW install

```bash
sudo apt-get update && sudo apt-get -y upgrade
sudo apt install python3-pip
sudo apt-get install python3-setuptools
wget https://github.com/BananoCoin/boompow/releases/download/v2.0.3/bpow-client-v203.zip
sudo apt install unzip
unzip bpow-client-v203.zip
cd bpow-client
pip3 install --user -r requirements.txt
sudo apt install ocl-icd-libopencl1
cd $HOME
```

or, if you want it all together, you can **enter this COMPLETE LINE**:

```bash
sudo apt-get update && sudo apt-get -y upgrade && sudo apt install -y python3-pip && wget https://github.com/BananoCoin/boompow/releases/download/v2.0.3/bpow-client-v203.zip && sudo apt install unzip && unzip -o bpow-client-v203.zip && cd bpow-client && pip3 install --user -r requirements.txt && sudo apt install ocl-icd-libopencl1 && cd ~
```

## Install nano-work-server

Compile the `nano-work-server` and copy it over:

```bash
sudo apt install ocl-icd-opencl-dev git && curl https://sh.rustup.rs -sSf | sh -s -- -y
git clone https://github.com/nanocurrency/nano-work-server.git
cd nano-work-server && cargo build --release && cd target/release
mkdir ~/bpow-client/bin/arm && cp -f nano-work-server ~/bpow-client/bin/arm && cd ~
```

## Usage

Start your bPoW with:

```bash
cd bpow-client
nohup ./bin/arm/nano-work-server --cpu-threads 4 -l 127.0.0.1:7000 && ¥
nohup python3 bpow_client.py --payout ban_###YOUR_ADDR_HERE### --work any --limit-logging
```

* If you do it with `nohup` you can close your cmd oder powershell window
* if you want to monitor it at specific time, just delete `nohup` and start without it
have fun ;)
* Do not expect much from overclocking, it is not worth it

*Have a nice crypto mining!*
