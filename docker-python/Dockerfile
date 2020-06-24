# 使用したいイメージを指定する
FROM python:3.7

COPY ./sample.py /usr/src/sample.py

# コンテナ上のワーキングディレクトリを指定する
WORKDIR /usr/src/

# RUNは"docker build"時に実行される
RUN echo "building..."

# CMDは"docker run"実行時に実行される
CMD python sample.py
