# How to setup Boom Pow! (bPoW) on Linux Mint

## Pre-requirements
- Linux Mint / debianoid installation (https://linuxmint.com)
- Banano-Address (https://vault.banano.cc)
- Banano-Boom PoW software (https://github.com/BananoCoin/boompow/releases)

## Install bPoW requirements
**Requirements are:**  
- python3: Interpreter for python. Version >= 3.6.7 (https://www.python.org)
- python3-pip: Package Installation program (https://pypi.org/project/pip)
- python3-setuptools: Setuptools for python3 (https://pypi.org/project/setuptools)
- unzip: extract tool for zip-files (https://packages.ubuntu.com/search?keywords=unzip&searchon=names)
- wget: download tool for linux (https://packages.ubuntu.com/search?keywords=wget&searchon=names)
- ocl-icd-libopencl1: Generic OpenCL ICD Loader (https://packages.ubuntu.com/search?keywords=ocl-icd-libopencl1&searchon=names)

**Installation:**  
The following commands installing the requirements for the bpow client, its dependencies and the bpow-client itself.   
To execute it create a folder at your computer change with a terminal into it and run the following lines.

```bash
sudo apt-get update -y
sudo apt-get install python3 -y 
sudo apt-get install python3-pip -y 
sudo apt-get install python3-setuptools -y 
sudo apt install unzip -y 
sudo apt install wget
wget https://github.com/BananoCoin/boompow/releases/download/v2.0.3/bpow-client-v203.zip
unzip bpow-client-v203.zip
cd bpow-client
pip3 install --user -r requirements.txt
sudo apt install ocl-icd-libopencl1

```
## Running the nano server (before the bpow_client.py)
At first the nano-work-server have to be started. This is done by changing into the subfolder "./bin/linux".   
There you find the executable. You could check if it runs with:
```bash
./nano-work-server –-help

```
If it succeed you will see the description of all parameters the program could understand.   
For this example we need the following parameters:
- -c Number CPU-Thread’s used for the nano-work-server (depending on your cpu)
- -g GPU Information (for this example it is 0:0)

**Now start the server executable with:**

```bash
./nano-work-server -c 4  -g 0:0

```

it should now report that the program is ready and in this example that it could use the gpu.
```
Initializing GPU: NVIDIA Corporation GeForce GTX 1080
Ready to receive requests.

```

## Running bpow_client.py
When the nano-work-server runs, open another terminal and change into the folder with the extracted bpow software. 
Check if the software runs with:
```bash
python3 bpow_client.py --help   
```
If it succeeds you will see the description of all parameters the program could understand.  
For this example we need the following parameters:

--payout  **your** Banano-Address  

**Now start the banano client with (replace ban_##### with your address):**  
Be sure that you typed your address correct! (Starting with ban_ ..., no typos)

```bash
python3 bpow_client.py --payout ban_#####

```

After you started the program it reports that its ready for work:
```
=======BoomPow (bPow)========
- Payouts to ban_#################
- Doing any work
- Server at wss://client:client@bpow.banano.cc/mqtt
- Work server at nano-work-server:7000, asynchronous requests enabled
- TO EXIT: Press CTRL+C
=============================


09:25:24 INFO: Checking for server availability...
09:25:25 INFO: Server online!
09:25:25 INFO: Setup successful, waiting for work


```
## Hints
Now you will see a lot of canceled requests. It’s not a bad sign. How many of them you see depends how often your computer won the race:  
1. getting request 
2. calculating proof of work 
3. send it back.


Yet you could wait for the payout...  
(every 12 hour starting at 8:00 UTC: a 10K ban pool is shared between all clients based on their work they provide) 

Or better visit the banano discord channel.   
There you could find further help, learn about banano and have a lot of fun. 


