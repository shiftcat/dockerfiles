FROM ubuntu:18.04

RUN apt-get update && yes | apt-get upgrade \
    && apt-get install -y build-essential \
    && apt-get install -y locales \
    && apt-get install -y python3 python3-pip openjdk-8-jre wget

## Timezone
ENV TZ Asia/Seoul

## 한글 설정
ENV LANGUAGE=ko_KR.UTF-8
ENV LANG=ko_KR.UTF-8

RUN locale-gen ko_KR ko_KR.UTF-8 \
    && update-locale LANG=ko_KR.UTF-8


RUN ln -s /usr/bin/python3 /usr/bin/python \
    && ln -s /usr/bin/pip3 /usr/bin/pip

## pip 설치
RUN pip install --upgrade pip

RUN pip install requests \
    && pip install bs4 \
    && pip install tqdm

## 데이터 분석 패키지 설치
RUN pip install matplotlib \
    && pip install numpy \
    && pip install pandas

## 데이터베이스 클라이언트 패키지 설치
RUN pip install redis \
    && pip install pymongo \
    && pip install elasticsearch

## 텍스트분석 패키지 설치
RUN pip install konlpy \
    && pip install jpype1

## 카프카 클라이언트 설치
RUN pip install kafka-python

## 주피터 노트북 설치
RUN pip install jupyter

## 주피터 실행 계정
RUN useradd -u 1000 jupyter \
    && mkdir /home/jupyter \
    && chown jupyter.jupyter /home/jupyter

USER 1000

RUN jupyter notebook --generate-config
RUN echo "c.NotebookApp.password = u'sha1:6a3f528eec40:6e896b6e4828f525a6e20e5411cd1c8075d68619'" >> /home/jupyter/.jupyter/jupyter_notebook_config.py

EXPOSE 8888

ENTRYPOINT jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser

