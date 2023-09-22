# 1 はじめに
こちらはrealtakahashiさんのgithubを元にM1 Mac用に作成しています。

https://github.com/realtakahashi/astar_docker_env?fbclid=IwAR1Eqso1--KG8qyOzQmPs5YsvKMJxyvOkPeHTS-4_P4M2jcLFjSpqCVmaIc

# 2 

まずは、こちらをgit cloneして下さい。

```git clone https://github.com/ytakahashi2020/flipper_docker_for_m1_mac.git```

次に、こちらのコマンドで、imageをビルドします。
20 ~ 30分程度かかると思われます。

```docker build -t astar_dev_env_v1 ./.devcontainer/```



```docker run -it -d -p 9944:9944 --name astar-dev astar_dev_env_v1```


```docker run -it -v $(pwd)/flipper_test:/app astar_dev_env_v1 /bin/bash```


```cd /app/contracts/flipper```

```cargo +nightly-2023-02-07 contract build```

# Description
- This Dockerfile implements the following environment:
  - rust language
  - cargo contract
  - node.js
  - npm
  - yarn
  - swanky

# How To Use
1. Please install docker in your environment.
1. Build docker image.
1. Create a docker container.
1. Enter into the container & build a WASM smart contract.

# Command Example
```
docker image build . -t astar_dev_env_v1
docker run -it -d -p 9944:9944 --name astar-dev astar_dev_env_v1
docker exec -it astar-dev /bin/bash
```

# Example Of Starting Swanky Node
```
./swanky-node --dev --tmp --ws-external
```

# Example Of Copying the file in docker container
```
docker cp 52e781bfaa38:/home/developer/flipper/target/ink/flipper.contract ./flipper.contract
```

