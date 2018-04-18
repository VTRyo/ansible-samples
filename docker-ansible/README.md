# Create docker imange with ansible and Packer

docker imageをansibleで作成する試みです。

ansible-containerというツールがansibleから公式で提供されていますが、まだ使いやすいとは言い切れない状態です。

そのため、packerとansibleを組み合わせてdokcer imageを作成してみました。

従来のサーバ構成管理でansibleを使用している場合には、わざわざdokcerfileを記述する必要がないので導入し易いのではないかと思います。

# Let's play DEMO

くわしくはこちらにも書いてあります。

[PackerとAnsibleでDocker imageを作る](https://tech.vtryo.me/create-dockerimage-packer-ansible/)

[PackerとAnsibleでDocker imageを作る(Remote Ansible編)](https://tech.vtryo.me/create-dockerimage-packer-remote-ansible/)

* 前提

・macOS<br>
・docker daemonが動いていること<br>
・packerがインストールされていること

## Fork

```
https://github.com/VTRyo/ansible-samples.git
```

## packer build

```
cd ansible-sample/dokcer-ansible
```

```
packer build container.json
```

実行後、イメージが作成されています。

## docker images

```
docker images
```

dokcer imagesの一覧でimageが作成されたか確認する。

## コンテナログイン

```
dokcer run -it <IMAGE ID> /bin/bash
```

ansibleでインストールしたパッケージが実行できるか確認してみるとよいです。
