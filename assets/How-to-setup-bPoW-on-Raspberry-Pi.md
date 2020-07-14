# How to setup bPoW on Raspberry Pi 
([posted on Discord by happy_haVoc, July 13th, 2020](https://discordapp.com/channels/415935345075421194/626058996578648065/732576731952840807))

## 1: setup raspbian (64 bit on RPI 3B and higher)
## 2: enable SSH
## 3: go to you Windows PC an connect via SSH to your raspberry
## 4: now you have to get Bpow:

- `sudo apt-get update && sudo apt-get -y upgrade`
- `sudo apt install python3-pip`
- `sudo apt-get install python3-setuptools`
- `wget https://github.com/BananoCoin/boompow/releases/download/v2.0.3/bpow-client-v203.zip`
- `sudo apt install unzip`
- `unzip bpow-client-v203.zip`
- `cd bpow-client`
- `pip3 install --user -r requirements.txt`
- `sudo apt install ocl-icd-libopencl1`
- `cd $HOME`

-or, if you want it all together, you can enter this COMPLETE LINE:
  -`sudo apt-get update && sudo apt-get -y upgrade && sudo apt install -y python3-pip && wget https://github.com/BananoCoin/boompow/releases/download/v2.0.3/bpow-client-v203.zip && sudo apt install unzip && unzip -o bpow-client-v203.zip && cd bpow-client && pip3 install --user -r requirements.txt && sudo apt install ocl-icd-libopencl1 && cd ~`

## 5: you need to compile nano-work server and copy it over

- `sudo apt install ocl-icd-opencl-dev git && curl https://sh.rustup.rs -sSf | sh -s -- -y`
- `git clone https://github.com/nanocurrency/nano-work-server.git`
- `cd nano-work-server && cargo build --release && cd target/release`
- `mkdir ~/bpow-client/bin/arm && cp -f nano-work-server ~/bpow-client/bin/arm && cd ~`

## 6. start you bpow:

- `cd bpow-client`
- `nohup ./bin/arm/nano-work-server --cpu-threads 4 -l 127.0.0.1:7000 & nohup python3 bpow_client.py --payout ban_###your adress here### --work any --limit-logging`

if you do it with NOHUP you can close your cmd oder powershell window
if you want to monitor it a specific time, just delete NOHUP and start without it
have fun :wink:
do not expect much from overclocking, it is not worth it
