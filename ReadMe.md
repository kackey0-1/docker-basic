# Dockerについて

## Docker Install
```bash
$ sudo yum -y update
$ sudo yum -y install docker
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
# -v "$PWD":/usr/src/test.py により、ホスト側のファイルをdockerコンテナ上の環境にも反映(ホスト側のパス:コンテナ側のパス) 
# ※$PWD は今いるディレクトリまでのパス
# -w /usr/src/test.py により、コンテナ上で作業する際のディレクトリを指定
# python:3.7 により、バージョン3.7のPythonのイメージを指定
# python test.py により、test.pyをPythonとして実行
$ docker run --rm -v "$PWD":/usr/src/test.py -w /usr/src/sample.py python:3.7 python sample.py
```

## Docker Execute Test from Dockerfile
```bash
$ cd docker-python
# -t オプションにより、作成されたイメージに適用するリポジトリ名
$ docker build -t sample-image .
$ docker run sample-image
```
