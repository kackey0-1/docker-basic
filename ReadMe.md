# Dockerについて

## Docker Install
```bash
# docker-engine   https://docs.docker.com/engine/install/
# docker-copmose  https://docs.docker.com/compose/install/ 
$ docker --version
$ sudo systemctl status docker
$ sudo systemctl start docker
$ sudo systemctl enable docker
```

## Docker Execute Test from Command Only
```bash
$ mkdir docker-python
$ cd docker-python
$ echo "print('Hello, from Docker container.')" > test.py
# docker run により、コンテナを起動
# -v "$PWD":/usr/src/sample.py により、ホスト側のファイルをdockerコンテナ上の環境にも反映(ホスト側のパス:コンテナ側のパス) 
# ※$PWD は今いるディレクトリまでのパス
# -w /usr/src/test.py により、コンテナ上で作業する際のディレクトリを指定
# python:3.7 により、バージョン3.7のPythonのイメージを指定
# python test.py により、test.pyをPythonとして実行
$ docker run --rm -v "$PWD":/usr/src/test.py -w /usr/src/test.py python:3.7 python test.py
```

## Docker Execute Test from Dockerfile
```bash
$ cd docker-python
# -t オプションにより、作成されたイメージに適用するリポジトリ名
$ docker build -t sample-image .
$ docker run sample-image

# 諸々コマンド
$ docker images
$ docker image ls
$ docker container ls
$ docker container stop <container_id>
$ docker container start <container_id>
$ docker exec -it <container_id> /bin/bash
```

## Docker Execute with docker-compose
`docker-compose` は、複数のDockerコンテナを使ってアプリケーションを立ち上げる際の管理をよしなにしてくれるツール
```bash
# up はbuild->pull->run をすべてやってくれる(-d はbackground実行オプション)
$ docker-compose up --build -d
# プロセスの状態確認(service名を指定可能 引数にservice名)
$ docker-compose ps
# プロセスの停止(service名を指定可能 引数にservice名)
$ docker-compose stop 
# プロセスの開始(service名を指定可能 引数にservice名)
$ docker-compose start
# コンテナ削除(service名を指定可能 引数にservice名)
$ docker-compose rm
```
