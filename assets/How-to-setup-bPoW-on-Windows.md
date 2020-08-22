# How to setup Boom Pow! (bPoW) on Windows

## Pre-requirements
- Microsoft Windows 7 / Microsoft Windows 10 installation
- Banano-Address (https://vault.banano.cc)
- Banano-Boom PoW software (https://github.com/BananoCoin/boompow/releases)

## Install bPoW requirements
**Requirements are:**  
- python3: Interpreter for python. Version >= 3.6.7 (https://www.python.org/downloads)
- python3-pip: Package Installation program (https://pypi.org/project/pip)

**Installation:**  
- If not installed install python3 **with** pip and adding it to the system variable path  
- - If you see a Windows error: 0xc000007b. You probably have to install the Microsoft Redistribution Pack 2015. It could found here: https://www.microsoft.com/en-gb/download/details.aspx?id=48145   

To check if python is working we could start it with the commandline (cmd.exe):
```cmd
python --version
```
It should resport a version number equal or greater than 3.6.7  
Then we start the same procedure for pip 
```cmd
pip --version
```
if both are working we could go to the next step.

## Edit the run_windows.bat 
This batch file is a startscript for bpow. Open it in notepad (editor).  
locate the line starting with set payout_address= and edit the Banano Address with **yours**.  
Be sure that you typed your address correct! (Starting with ban_ ..., no typos)  
Save the file and close the notepad.

## Starting the run_windows.bat
Start the batchfile by double clicking it. Two commandline windows should pop up.

## Hints
Now you will see a lot of canceled requests. It’s not a bad sign. How many of them you see depends how often your computer won the race:  
1. getting request 
2. calculating proof of work 
3. send it back.


Yet you could wait for the payout...  
(every 12 hour starting at 8:00 UTC: a 10K ban pool is shared between all clients based on their work they provide) 

Or better visit the banano discord channel.   
There you could find further help, learn about banano and have a lot of fun. 

