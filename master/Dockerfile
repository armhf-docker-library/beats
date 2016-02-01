FROM armhfbuild/golang:1.5.3

RUN mkdir /src /build \
  && cd /src \
  && git clone https://github.com/elastic/beats.git . \
  && go get github.com/elastic/beats/libbeat/beat \
  && cd /src/filebeat \
  && make \
  && cp --target-directory /build filebeat filebeat.yml \
  && cd /src/topbeat \
  && make \
  && cp --target-directory /build topbeat topbeat.yml \
  && cd /src/packetbeat \
  && apt-get update && apt-get install -y libpcap0.8-dev \
  && make \
  && cp --target-directory /build packetbeat packetbeat.yml
  # && rm -rf /src

RUN ls -l /build
