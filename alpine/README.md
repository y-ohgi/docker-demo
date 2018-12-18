# About
AlpineLinuxベースでPHPのDockerイメージを作成する

# Demo
## 1. イメージのビルド
```
$ cd /path/to/docker-demo
$ docker build -t myphp -f ./php/Dockerfile ./php
$ docker build -t myphp:alpine -f ./alpine/Dockerfile ./alpine
```

## 2. イメージの確認
```
$ docker images
$ docker images | grep myphp
myphp               alpine              b9569504a15d        3 minutes ago       78.5MB
myphp               latest              c6fa3bcfe6aa        3 minutes ago       371MB
```

## 3. コンテナの起動
```
$ docker run -d -p 9000:9000 myphp:alpine
$ open http://localhost:9000/phpinfo.php
```

[PHP 7.3.0 - phpinfo()](http://localhost:9000/phpinfo.php)
