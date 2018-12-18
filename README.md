docker-demo
---


# About
Docker勉強会のデモ用コード

# Environment
* [Play with Docker](https://labs.play-with-docker.com/)
    - ブラウザでDockerを実行する環境
    - DockerHubのIDが必要
        - [Docker Hub](https://hub.docker.com/)

## Info
* Docker for Windows/Macでも可

# Demo
## 1. Dockerイメージのpull
`nginx` のDockerイメージをDockerHubからpullする

```
$ docker pull nginx
```

nginxのイメージがpullできているか確認

```
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              568c4670fa80        2 weeks ago         109MB
```

## 2. Dockerコンテナの作成
pullしたnginxを起動する

```bash
$ docker run \
    -p 8080:80 \
    -d \
    nginx
```

`-p` : ホストの8080ポートへ、起動したコンテナの80ポートをフォワードさせる  
`-d` : バックグラウンドで実行  
`nginx` : 起動するイメージ名


## 3. nginxが起動できているか確認
[localhost:8080](http://localhost:8080/) へアクセスし、nginxが起動できているか確認

```
$ curl -I localhost:8080
HTTP/1.1 200 OK
Server: nginx/1.15.7
Date: Tue, 18 Dec 2018 20:53:38 GMT
Content-Type: text/html
Content-Length: 612
Last-Modified: Tue, 27 Nov 2018 12:31:56 GMT
Connection: keep-alive
ETag: "5b393c-264"
Accept-Ranges: bytes
```

## 4. Dockerfileからイメージの作成
GitHubから当該リポジトリをクローン
```
$ git clone https://github.com/y-ohgi/docker-demo
$ cd docker-demo/php
```

[php/Dockerfile](php/Dockerfile) をもとにDockerイメージをビルド
```
$ docker build \
    -t myphp \
    .
```

`-t` : Dockerイメージ名
`.` : コンテキストとなるディレクトリを指定

## 5. 作成したイメージの実行

```
$ docker run \
    -p 9000:9000 \
    -d \
    myphp
```

[localhost:9000/phpinfo.php](http://localhost:9000/phpinfo.php) へアクセスし、PHPが起動できているか確認  
同時にPDOがインストールされているかも確認する


# Tips
## 起動したコンテナを停止
```
# 起動中のコンテナを確認
$ docker ps

# 全てのコンテナを停止
$ docker stop $(docker ps -aq)

# コンテナの停止を確認
$ docker ps
```


# 手前味噌
[y-ohgi/dockerfiles](https://github.com/y-ohgi/dockerfiles)
