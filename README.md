# my-first-substrate-project-series-III-part-2

# We Are Going To Run a Local Node Using Docker  
  
We need a local ```volume``` for the polkadot docker container.  
```
mkdir -p ${HOME}/MySoftwareProjects/blockchain/rust/rust-substrate-blockchain-projects/polkadot-substrate-docker-volume;
```
  
Set a variable to be used in the ```docker run``` command.  
```  
MY_LOCAL_FOLDER=${HOME}/MySoftwareProjects/blockchain/rust/rust-substrate-blockchain-projects/polkadot-substrate-docker-volume;  
```
  
Let's run this:
```
sudo docker run -d \
    --cpus="0.5" \
    --memory="512m" \
    --name "MyPolkadotContainer"  \
    -p 9933:9933 \
    -p 9944:9944 \
    -v ${MY_LOCAL_FOLDER}:/polkadot \
    parity/polkadot:latest
```
