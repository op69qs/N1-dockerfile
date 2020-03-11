FROM arm64v8/ubuntu:18.04


ARG  NAIVEPROXY_VER=v80.0.3987.87-3
ARG  TARGET_BUILD=arm64
ENV TZ=Asia/Shanghai

RUN apt-get update && \
apt-get install --no-install-recommends -y libnss3 ca-certificates wget xz-utils

RUN   mkdir /naiveproxy  \
&&   wget https://github.com/klzgrad/naiveproxy/releases/download/${NAIVEPROXY_VER}/naiveproxy-${NAIVEPROXY_VER}-linux-${TARGET_BUILD}.tar.xz  -O /naiveproxy/naiveproxy.tar.xz \
&&   tar -xvJf /naiveproxy/naiveproxy.tar.xz  -C  /naiveproxy  \
&&   mv /naiveproxy/naiveproxy-${NAIVEPROXY_VER}-linux-${TARGET_BUILD}/* /naiveproxy/ 


RUN apt-get remove -y --auto-remove ca-certificates wget xz-utils && \
apt-get clean && \
rm -rf /var/lib/apt/lists/* /naiveproxy/naiveproxy-${NAIVEPROXY_VER}-linux-${TARGET_BUILD}/ /naiveproxy/naiveproxy.tar.xz

ENTRYPOINT [ "/naiveproxy/naive" ]

WORKDIR /naiveproxy
VOLUME /config

CMD [ "/config/config.json" ]
