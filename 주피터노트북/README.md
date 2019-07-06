# 주피터 노트북

### Docker build & run

```
docker build -t myjupyter:0.1 .

docker run -d --net=host -p 8888:8888 -v ${HOME}/jupyter:/jupyter myjupyter:0.1

```

* localhost:8888

* 암호: root

