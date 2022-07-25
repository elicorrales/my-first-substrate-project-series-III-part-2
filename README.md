# my-first-substrate-project-series-III-part-2

# We Are Going To Run a Local Node Using Docker  
  
We need a local ```volume``` for the polkadot docker container.  
```  
MY_LOCAL_FOLDER=${HOME}/MySoftwareProjects/blockchain/rust/rust-substrate-blockchain-projects/polkadot-substrate-docker-volume;  
```
  
Your basic run command:  
```
docker run -d \
    -p 30333:30333 \
    -p 9933:9933 \
    -v ${MY_LOCAL_FOLDER}:/polkadot \
    parity/polkadot:latest \
    --chain westend \
    --rpc-external \
    --rpc-cors all  
```

Or, if you wish to add a name to the container:  
```
docker run -d \
    -p 30333:30333 \
    -p 9933:9933 \
    -v ${MY_LOCAL_FOLDER}:/polkadot \
    parity/polkadot:latest \
    --chain westend \
    --rpc-external \
    --rpc-cors all \
    --name "PolkaDocker"  
```
  
If (probably should) you want to limit your CPU and memory usage:  
```
docker run -d \
    -p 30333:30333 \
    -p 9933:9933 \
    -p 9944:9944 \
    -v ${MY_LOCAL_FOLDER}:/polkadot \
    parity/polkadot:latest \
    --chain westend \
    --ws-external \
    --rpc-external \
    --rpc-cors all \
    --name "PolkaDocker"  \
    --cpus=".5" --memory="512m"
```

