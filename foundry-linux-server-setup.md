# Foundry VTT Linux Server Setup

## Create Linux VM
- vm settings to be determined
- add inbound port rule
  - source : *
  - destination : 24670 
  - protocol : TCP

## Install Tools on VM
- open a bash terminal
- ssh into the terminal
  - `ssh <username>@<vm's ip address>`
- run the following commands:
  - `sudo apt-get update`
  - `sudo apt install make`
  - `sudo apt install gcc`
    - this one is only required for running no ip
  - `sudo apt install unzip`
  - `wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash`
  - `source ~/.bashrc`
  - `nvm install nvm install v12.17.0`

## Download FoundryVTT
- download the foundry nodejs zip to your device
- open a bash terminal
- copy the zip into the vm previously created
  - `scp foundryvtt-0.6.0.zip <username>@<vm's ip address>`
- ssh into the vm
- unzip `foundryvtt-0.6.0.zip` into a desired location
  - `unzip foundryvtt-0.6.0.zip -d foundry/bin/foundryvtt-0.6.0/`
- create foundry vtt data folder
  - `mkdir foundry/data`  
  
## Setup NoIp service
### Reserve Hostname on No IP
- create account on https://www.noip.com/
- reserve a host name
  - I recommend using a free domain such as "servegame.com"
  - there are other domains to pick from as well
  - I am using "foundry.servegame.com" as an example here

### Setup VM to out update its IP address
This will allow you to access your foundry vtt instance via an url like this:
- http://foundry.servegame.com:24670

Here are the full instructions:
- https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/

It basically sums up to these steps:
- `cd /usr/local/src/`
- `sudo wget http://www.noip.com/client/linux/noip-duc-linux.tar.gz`
- `sudo tar xf noip-duc-linux.tar.gz`
- `cd noip-2.1.9-1/`
- `sudo make install`
  - you will be prompted with:
    - login/email for noip.com
    - password for the above login/email noip.com account
    - if you want to sync all host names to this machine - pick no : N
      - it will then ask if you want to update for each of the host names you have in the account. Say yes to the one you want
      - in our case : `foundry.servegame.com`
    - how often you want to update the host with the VM's ip address
      - pick the default : 30
- `sudo /usr/local/bin/noip2 -C`
  - you will be prompted again with the same questions
- `sudo /usr/local/bin/noip2` 
    
 
## Start Server
- open a bash terminal and ssh into the server
  - `ssh <username>@<vm's ip address>`
- start foundry vtt server
  - `node $HOME/foundry/bin/foundryvtt-0.6.0/resources/app/main.js --dataPath=$HOME/foundry/data --port=24670`
