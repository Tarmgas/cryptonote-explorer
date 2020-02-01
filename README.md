The Cryptonote Explorer
============

[![AngularJS](https://img.shields.io/badge/1.6.5-green.svg?logo=angular&label=angularjs&style=for-the-badge)](https://code.angularjs.org/1.6.5/docs/misc/downloading)
[![NodeJS](https://img.shields.io/badge/8.6.0-green.svg?logo=node.js&label=nodejs&style=for-the-badge)](https://nodejs.org/en/download/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](http://makeapullrequest.com)
[![Build passing](https://img.shields.io/appveyor/ci/gruntjs/grunt.svg?style=for-the-badge)](http://makeapullrequest.com)

See it live on [**alloyexplorer.com**](https://alloyexplorer.com)

This is a **Blockchain Explorer** initially designed for tracking the [**Alloy [XAO]**](https://alloyproject.org)  services and network status but currently supporting a growing number of cryptocurrencies.

#### Operations flow
The explorer gathers data from the `coin daemon` and `compatible pools` via `rpc`, processes everything, saves to a `mongodb` collection and uses `websockets` to send stats over to a nice `angularjs` frontend.

#### Goal
Provide a set of open-sourced services that I believe should be available by default for any existing cryptocurrency.

#### Available services
- [x] **Blockchain Explorer**
- [x] **Live Blockchain Transactions**
- [x] **Pools Tracker**
- [x] **Profitability Calculator**
- [x] **Remote Nodes Tracker**
- [x] **Paper Wallet Generator**
- [x] **Exchange integration**
  - [**Tradeogre**](https://tradeogre.com)
- [x] **API**

#### Extra services
- [ ] **Mining Pool**

#### Upcoming services
- [ ] **Web Miner**
- [ ] **Web Transit Wallet**
- [ ] **Alert/Info System**
- [ ] **Daily Blockchain Backup**
- [ ] **More exchanges**
- [ ] **More coins**
- [ ] **Documentation**

## Screenshots
> **Important:** A live version of this explorer can be found @ [https://alloyexplorer.com](https://alloyexplorer.com)

![Screenshot](https://cdn.explorer.sh/cnexplorer/01-cnexplorer-home.jpg "Home")

![Screenshot](https://cdn.explorer.sh/cnexplorer/02-cnexplorer-mempool.jpg "Mempool")

![Screenshot](https://cdn.explorer.sh/cnexplorer/03-cnexplorer-pools.jpg "Pools Monitor")

![Screenshot](https://cdn.explorer.sh/cnexplorer/04-cnexplorer-remotes.jpg "Remotes Monitor")

![Screenshot](https://cdn.explorer.sh/cnexplorer/05-cnexplorer-paperwallet.jpg "Paper Wallet")

## Prerequisites
> Click on a shield to go to the downloads page

[![NodeJS](https://img.shields.io/badge/8.6.0-green.svg?logo=node.js&label=nodejs&style=for-the-badge)](https://nodejs.org/en/download/)
[![MongoDB](https://img.shields.io/badge/3.4.4-green.svg?logo=mongodb&label=mongodb&style=for-the-badge)](https://www.mongodb.com/download-center/community)
[![NPM](https://img.shields.io/badge/5.4.2-green.svg?logo=npm&label=npm&style=for-the-badge)](https://nodejs.org/en/download/)
[![grunt-cli](https://img.shields.io/badge/1.2.0-green.svg?label=grunt-cli&style=for-the-badge)](https://gruntjs.com/getting-started#installing-the-cli)

### Installation ###
git clone https://github.com/Tarmgas/cryptonote-explorer
```bash
cd cryptonote-explorer
npm update
npm install
sudo npm i -g grunt grunt-cli
```

To build run
```bash
grunt build
```
		
api via mongodb.

install mongodb:
```bash
    sudo apt update
    sudo apt install -y mongodb
    ```
check status / start / stop / restart
```bash
    sudo systemctl status mongodb
    ```
open default port 27017 in firewall
```bash
    sudo ufw allow 27017
    ```
change bind ip/port, remember comma: run: sudo nano /etc/mongodb.conf
```bash
bind_ip = 127.0.0.1,192.168.1.100
```
```bash
sudo systemctl restart mongodb
```

Create user and make database:  
in terminal write: mongo
---first change to admin db and make adminuser.
```bash
use admin
db.createUser({user:"admin",pwd:"Balletryne20",roles:["root"]})
```

---create coin databse and user
```bash
use COIN
db.createUser({user: "coinuser",pwd: "P4ssw0rd",roles: [{ role: "readWrite", db: "GNS" }]})
```

---howto delete user:       
```bash
db.dropUser("username")
```

## Config
> This example config file is located under `lib/config-example.js`
> After entering your own data, save the file under `lib/config.js`

### run: npm start ###



OLD: ## Installation
> **Important:** Make sure you have the above dependencies installed.

```bash
apt install git -Y
git clone https://github.com/kh4n-ro/cryptonote-explorer
cd cryptonote-explorer
npm update
npm install
sudo npm i -g grunt grunt-cli
```

To build run
```bash
grunt build
```

## Config
> This example config file is located under `lib/config-example.js`
> After entering your own data, save the file under `lib/config.js`

```bash
module.exports = {
  "NAME": "Alloy Explorer",
  "ADMIN": {
    "USERNAME": "ADMIN_USERNAME",
    "PASSWORD": "SOME_SECRET_PASSWORD",
    "SECRET": "SOME_SECRET_LONG_STRING"
  },
  "EMAIL": "ADMIN_EMAIL",
  "DB": {
    "HOST": "localhost",
    "DBNAME": "DATABASE_NAME",
    "RETRIES": 50
  },
  "FRONTEND": {
    "HOST": "alloyexplorer.com",
    "PORT": 12401,
    "TOKEN_EXPIRATION": 1200,
     "SSL" : {
       "ENABLED": false,
       "secureOptions": constants.SSL_OP_NO_SSLv3 | constants.SSL_OP_NO_SSLv2,
       "key": key,
       "cert": cert,
       "dhparam": dh
     }
  },
  "DAEMON": {
    "PROTOCOL" : "http",
    "HOST" : "193.37.138.140",
    "PORT" : 1811,
  },
  "REMOTES" : [{
    hostname : 'rpc.alloyproject.org',
    ip : '195.201.35.225',
    port : 1811
  }],
  "ALGORITHM"       : "cn/alloy",
  "LOCALPOOL"       : "",
  "WEBMINER"        : "",
  "PAPERWALLET"     : {
    coinUnitPlaces    : 12,
    coinSymbol        : 'XAO',
    coinName          : 'Alloy',
    coinUriPrefix     : 'alloy:',
    addressPrefix     : 54
  },
  "MINING_APPS"     : [
    {
      "NAME"       :  "XMR-Stak-Alloy",
      "LINK"       :  "https://github.com/alloyproject/xmr-stak-alloy/releases",
    },{
      "NAME"       :  "SRBMiner",
      "LINK"       :  "https://bitcointalk.org/index.php?topic=3167363.0",
    },{
      "NAME"       :  "xmrig-nvidia",
      "LINK"       :  "https://github.com/alloyproject/xmrig-nvidia/releases",
    }
  ],
  "BENCHMARKS"      : [
    {
      "MANUFACTURER" : "Intel",
      "TYPE"  : "CPU",
      "MODEL" : "I7-3770",
      "CONSUMPTION" : 92,
      "MEMORY" : 0,
      "HASHRATE" : 150
    },{
      "MANUFACTURER" : "AMD",
      "TYPE"  : "GPU",
      "MODEL" : "RX550",
      "CONSUMPTION" : 40,
      "MEMORY" : 2,
      "HASHRATE" : 220
    },{
      "MANUFACTURER" : "AMD",
      "TYPE"  : "GPU",
      "MODEL" : "RX550",
      "CONSUMPTION" : 43,
      "MEMORY" : 4,
      "HASHRATE" : 220
    },
  ],
  "BLOCKTARGETINTERVAL" : 180,
  "HISTORY_BLOCKS_LEN" : 64,
  "GET_POOLS_SECONDS" : 60,
  "GET_MEMPOOL_SECONDS" : 10,
  "GET_INFO_SECONDS" : 5,
  "GET_BLOCKSLIST_MINUTES" : 1,
  "LIGHT_BLOCKS_HISTORY" : 15,
  "HISTORY_CHART_MINUTES" : 30,
  "EXCHANGE_UPDATE_INTERVAL" : 60,
  "TO_TICKER" : "BTC-XAO",
  "EXCHANGES" : [
    {
      "NAME" : "TRADEOGRE",
      "URL" : "https://tradeogre.com/api/v1/markets"
    }
  ],
  "COINUNITS" : Math.pow(10, 12),
  "MAXSUPPLY" : 84000000, // 84M
  "SYMBOL" : "XAO",
  "HIDE_DOMINANT_POOLS" : true,
  "DOMINANCE_PERCENT" : 40,
  "POOLS" : [{
    "frontend": "xao.mine2gether.com",
    "api": "https://xao.mine2gether.com/api/stats",
    "rootapi": "https://xao.mine2gether.com/api/stats",
    "color": "#B45F04",
    "v": 1
  }],
  "VERBOSITY" : 2
}
```
## Run
```bash
npm start
```

Keep in mind that this app is still in its `early Alpha` stage of development.
Still many features to be added.
