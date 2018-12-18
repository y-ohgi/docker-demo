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
    -p 8080:80 \ # ホストの8080ポートへ、起動したコンテナの80ポートをフォワードさせる
    -d \         # バックグラウンドで実行
    nginx        # 起動するイメージを指定
```

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

# Tips
## 起動したコンテナを停止
```
$ docker stop $(docker ps -aq)
```
