# my-first-substrate-project-series-III-part-2

# We Are Going To Run a Local Node Using Docker  
  
[Here](https://github.com/elicorrales/blockchain-tutorials/blob/main/How-To-Setup-Docker-WSL-Ubuntu.md) is how to setup Docker (engine) only on WSL Ubuntu without using/installing Docker Desktop.  

Caviat: (2022-07-24) I was not able to get the daemon to start in Ubuntu 22.04, and when installing and trying to ```sudo apt update``` Ubuntu 21.04, there was a release repositories issue, so I punted back to Ubuntu 20.04
<br/>

We need a local ```volume``` for the polkadot docker container.  
```
mkdir -p ${HOME}/MySoftwareProjects/blockchain/rust/rust-substrate-blockchain-projects/polkadot-substrate-docker-volume;
```
  
Set a variable to be used in the ```docker run``` command.  
```  
MY_LOCAL_FOLDER=${HOME}/MySoftwareProjects/blockchain/rust/rust-substrate-blockchain-projects/polkadot-substrate-docker-volume;  
```
  
This will create and start up a local docker node for HTTP only:
```
sudo docker run -d \
    --cpus="0.5" \
    --memory="1024m" \
    --name "MyLocalPolkaDockerHttpNode"  \
    -p 9933:9933 \
    -v ${MY_LOCAL_FOLDER}:/polkadot \
    parity/polkadot:latest \
    --rpc-external
```

This will create and start up a local docker node for WS only:
```
sudo docker run -d \
    --cpus="0.5" \
    --memory="1024m" \
    --name "MyLocalPolkaDockerWsNode"  \
    -p 9944:9944 \
    -v ${MY_LOCAL_FOLDER}:/polkadot \
    parity/polkadot:latest \
    --ws-external
```
  
  
