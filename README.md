# NOMP KawPoW Algorithm Pool 
# fork pool Satoex , ProcyonCoin
Highly Efficient mining pool for Coins based on KawPoW algo!

This is opensource mining pool for Redecoin

-------
### Screenshots
#### Home<br />
![Home](https://raw.githubusercontent.com/Satoex/kawpow-pool/master/docs/frontend/home.png)

#### Pool Stats<br />
![Pool Stats](https://raw.githubusercontent.com/Satoex/kawpow-pool/master/docs/frontend/poolstats.png)<br /><br />

#### Miner Stats<br />
![Miner Stats](https://raw.githubusercontent.com/Satoex/kawpow-pool/master/docs/frontend/minerstats.png)<br /><br />

#### Payments<br />
![Payments](https://raw.githubusercontent.com/Satoex/kawpow-pool/master/docs/frontend/payments.png)<br /><br />

-------
### Node Open Mining Portal consists of 3 main modules:
| Project | Link |
| ------------- | ------------- |
| [Stratum Pool](https://github.com/tweetyf/kawpow-stratum-pool.git) | https://github.com/tweetyf/kawpow-stratum-pool.git |
| [Node Multihashing](https://github.com/zone117x/node-multi-hashing.git) | https://github.com/zone117x/node-multi-hashing.git |

-------
### Requirements
***NOTE:*** _These requirements will be installed in the install section!_<br />
* Ubuntu Server 18.04.* LTS
* Coin daemon
* Node Version Manager
* Node 12.13.0
* Process Manager 2 / pm2
* Redis Server
* ntp

-------

### Install Pool

    sudo apt install git -y
    cd
    git clone https://github.com/jakubartur/kawpow-rede-pool.git 
    cd kawpow-rede-pool/
    ./install.sh

-------
### Configure Pool

Change "stratumHost": "192.168.0.200", to your IP or DNS in file config.json:

    cd ~/kawpow-pool
    nano config.json

```javascript
{
    
    "poolname": "Redecoin Pool",
    
    "devmode": false,
    "devmodePayMinimim": 0.25,
    "devmodePayInterval": 120,
    
    "logips": true,       
    "anonymizeips": true,
    "ipv4bits": 16,
    "ipv6bits": 16,
    "poolwarningmsg": "",
    
    "defaultCoin": "neoxacoin",
    
    "poollogo": "/static/icons/redecoin.png",
    
    "discordtwitterfacebook": "",
    
    "pagetitle": "Coin Pool - 1% Fees",
    "pageauthor": "kawpow project",
    "pagedesc": "A reliable, 0% fee, easy to use mining pool for cryptocurrency! No matter your experience with mining cryptocurrency, we make it easy! Get started mining today!",
    "pagekeywds": "GPU,CPU,Hash,Hashrate,Cryptocurrency,Crypto,Mining,Pool,Bitcoin,Redecoin,Procyon,Wavi,Wavicoin,Dixicoin,Dixi,QBic,QBicCoin,Easy,Simple,How,To",

    "btcdonations": "",
    "ltcdonations": "",
    "ethdonations": "",

    "logger" : {
        "level" : "debug",
        "file" : "./logs/nomp_debug.log"
    },

    "cliHost": "127.0.0.1",
    "cliPort": 17117,

    "clustering": {
        "enabled": false,
        "forks": "auto"
    },

    "defaultPoolConfigs": {
        "blockRefreshInterval": 1000,
        "jobRebroadcastTimeout": 55,
        "connectionTimeout": 600,
        "emitInvalidBlockHashes": false,
        "validateWorkerUsername": true,
        "tcpProxyProtocol": false,
        "banning": {
            "enabled": true,
            "time": 600,
            "invalidPercent": 50,
            "checkThreshold": 500,
            "purgeInterval": 300
        },
        "redis": {
            "host": "127.0.0.1",
            "port": 6379
        }
    },

    "website": {
        "enabled": true,
        "sslenabled": false,
        "sslforced": false,
        "host": "0.0.0.0",
        "port": 8080,
        "sslport": 443,
        "sslkey": "~/nomp-kawpow-pool/certs/privkey.pem",
        "sslcert": "~/nomp-kawpow-pool/certs/fullchain.pem",
        "stratumHost": "192.168.100.105",
        "stats": {
            "updateInterval": 30,
            "historicalRetention": 172800,
            "hashrateWindow": 600
        },
        "adminCenter": {
            "enabled": false,
            "password": "NOT_WORKING_YET_:P_LESHACAT_CAN_DO_ADMIN_PANEL_FUNCTIONALITY_TOO"
        }
    },

    "redis": {
        "host": "127.0.0.1",
        "port": 6379
    },

    "switching": {
        "switch1": {
            "enabled": false,
            "algorithm": "sha256",
            "ports": {
                "3333": {
                    "diff": 10,
                    "varDiff": {
                        "minDiff": 16,
                        "maxDiff": 512,
                        "targetTime": 15,
                        "retargetTime": 90,
                        "variancePercent": 30
                    }
                }
            }
        },
        "switch2": {
            "enabled": false,
            "algorithm": "scrypt",
            "ports": {
                "4444": {
                    "diff": 10,
                    "varDiff": {
                        "minDiff": 16,
                        "maxDiff": 512,
                        "targetTime": 15,
                        "retargetTime": 90,
                        "variancePercent": 30
                    }
                }
            }
        },
        "switch3": {
            "enabled": false,
            "algorithm": "x11",
            "ports": {
                "5555": {
                    "diff": 0.001,
                    "varDiff": {
                        "minDiff": 0.001,
                        "maxDiff": 1, 
                        "targetTime": 15, 
                        "retargetTime": 60, 
                        "variancePercent": 30 
                    }
                }
            }
        }
    },

    "profitSwitch": {
        "enabled": false,
        "updateInterval": 600,
        "depth": 0.90,
        "usePoloniex": true,
        "useCryptsy": true,
        "useMintpal": true,
        "useBittrex": true
    }

}
```
Create a pool config for you coins:
    
    mv pool_configs/neoxa_example.json pool_configs/neoxa.json

Change "address": "GXUJSRkFHc6AJXMRyZTcA1xorKkXpU2RRe", to your pool created wallet address in file neoxa.json:

    cd pool_configs
    nano neoxa.json

```javascript
{
    "enabled": true,
    "coin": "neoxa.json",

    "address": "GXUJSRkFHc6AJXMRyZTcA1xorKkXpU2RRe",
    
    "donateaddress": "GXUJSRkFHc6AJXMRyZTcA1xorKkXpU2RRe",

    "rewardRecipients": {
	    "GXUJSRkFHc6AJXMRyZTcA1xorKkXpU2RRe":0.5
    },

    "paymentProcessing": {
        "enabled": true,
        "schema": "PROP",
        "paymentInterval": 300,
        "minimumPayment": 5,
        "maxBlocksPerPayment": 50000,
        "minConf": 30,
        "coinPrecision": 8,
        "daemon": {
            "host": "127.0.0.1",
            "port": 9766,
            "user": "user1",
            "password": "pass1"
        }
    },

    "ports": {
		"10001": {
            "diff": 0.001,
    	    "varDiff": {
    	        "minDiff": 0.001,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10002": {
            "diff": 0.01,
    	    "varDiff": {
    	        "minDiff": 0.01,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10003": {
            "diff": 0.1,
    	    "varDiff": {
    	        "minDiff": 0.1,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10004": {
            "diff": 0.5,
    	    "varDiff": {
    	        "minDiff": 0.5,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10005": {
            "diff": 1,
    	    "varDiff": {
    	        "minDiff": 1,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10006": {
            "diff": 2,
    	    "varDiff": {
    	        "minDiff": 2,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10007": {
            "diff": 4,
    	    "varDiff": {
    	        "minDiff": 4,
    	        "maxDiff": 64,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        },
		"10008": {
            "diff": 0.5,
    	    "varDiff": {
    	        "minDiff": 0.5,
    	        "maxDiff": 32,
    	        "targetTime": 10,
    	        "retargetTime": 60,
    	        "variancePercent": 30,
    		    "maxJump": 25
    	    }
        }
    },

    "daemons": [
        {
            "host": "127.0.0.1",
            "port": 9766,
            "user": "user1",
            "password": "pass1"
        }
    ],

    "p2p": {
        "enabled": false,
        "host": "127.0.0.1",
        "port": 19333,
        "disableTransactions": true
    },

    "mposMode": {
        "enabled": false,
        "host": "127.0.0.1",
        "port": 3306,
        "user": "me",
        "password": "mypass",
        "database": "ltc",
        "checkPassword": true,
        "autoCreateWorker": false
    },

    "mongoMode": {
        "enabled": false,
        "host": "127.0.0.1",
        "user": "",
        "pass": "",
        "database": "ltc",
        "authMechanism": "DEFAULT"
    }

}

```

### Run Pool
    
    node ./init.js
# kawpow-rede-pool
