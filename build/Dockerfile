FROM ubuntu:18.04 AS build
RUN apt-get update 
RUN apt-get install -y make
RUN apt-get install -y gcc gcc-multilib
RUN apt-get install -y clang
RUN apt-get install -y libpam0g-dev
RUN apt-get install -y unzip

COPY skalibs-2.14.3.0.zip /tmp/
COPY execline-2.9.6.1.zip /tmp/
COPY s6-dns-2.4.0.0.zip /tmp/
COPY s6-2.13.1.0.zip /tmp/
COPY s6-networking-2.7.0.4.zip /tmp/


WORKDIR /tmp

RUN cd /tmp && unzip execline-2.9.6.1.zip 
RUN cd /tmp && unzip skalibs-2.14.3.0.zip
RUN cd /tmp && unzip s6-dns-2.4.0.0.zip
RUN cd /tmp && unzip s6-2.13.1.0.zip
RUN cd /tmp && unzip s6-networking-2.7.0.4.zip

RUN cd /tmp/skalibs-2.14.3.0 && ./configure && make && make install
RUN cd /tmp/execline-2.9.6.1 && ./configure && make && make install
RUN cd /tmp/s6-dns-2.4.0.0 && ./configure && make && make install
RUN cd /tmp/s6-2.13.1.0 && ./configure && make && make install
RUN cd /tmp/s6-networking-2.7.0.4 && ls /usr/lib | grep s6 && ./configure && make && make install

RUN apt-get install -y zip
COPY install.sh /tmp/s6/install.sh
RUN cp /bin/s6-tcpserver /tmp/s6/ && \
    cp /bin/s6-tcpserver-socketbinder /tmp/s6 && \
    cp /bin/s6-tcpserverd /tmp/s6 && \
    cp /lib/libskarnet.so.2.14 /tmp/s6/ && \
    zip -r /tmp/s6.zip s6

FROM ubuntu:22.04

COPY  --from=build /bin/s6-tcpserver   /bin/s6-tcpserver
COPY  --from=build /lib/libskarnet.so.2.14 /lib/libskarnet.so.2.14
COPY  --from=build /tmp/s6.zip /s6.zip