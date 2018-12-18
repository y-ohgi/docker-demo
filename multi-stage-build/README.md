Multi Stage Build
---

# About
Dockerのマルチステージビルドを用いて軽量なイメージを作成するサンプル

# Demo
## 1. シングルステージビルド

```
$ cd /path/to/multi-stage-build
$ docker build -t mygo .
$ docker run mygo
Hello world!
```

## 2. マルチステージビルド

```
$ docker build -t mygo:multi -f Dockerfile.multi .
$ docker run mygo:multi
Hello world!
```

## 3. イメージサイズの確認
```
$ docker images | grep mygo
mygo                latest              c72daca8f226        About a minute ago   312MB
mygo                multi               cb6bc59dc0ce        About a minute ago   6.32MB
```

`312MB` → `6.32MB`

# 参照
* [Use multi-stage builds | Docker Documentation](https://docs.docker.com/develop/develop-images/multistage-build/#use-multi-stage-builds)
