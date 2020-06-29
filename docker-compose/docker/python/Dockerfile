# 使用するPythonのイメージを指定する
FROM python:3.7
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# ワーキングディレクトリを指定する
WORKDIR /python/src/django

# 必要なパッケージなどなどをインストールする
RUN pip install --upgrade pip
ADD ./docker/python/requirements.txt /python/src/django/
RUN pip install -r requirements.txt

# sample_docker_compose_python直下のディレクトリをコンテナ上に載せる
ADD . .
