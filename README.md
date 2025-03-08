# s6-tcpserver

s6-tcpserver compiled for ubuntu


## Build


```
docker-compose build 
docker run --rm -it -v.:/export ctf-ubuntu-s6 cp /s6.zip /export
```


## Install local

```
wget "https://github.com/jossets/s6-tcpserver/raw/refs/heads/main/s6.zip" -O /tmp/s6.zip &&\
  cdc /tmp &&\
  unzip s6.zip &&\
  cd s6 &&\
  chmod a+x install.sh &&\
  ./install.sh
```

