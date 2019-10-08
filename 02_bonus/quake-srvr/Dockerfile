FROM alpine:latest as builder

RUN \
  echo "# INSTALL DEPENDENCIES ##########################################" && \
  apk --no-cache add curl g++ gcc git make && \
  mkdir -p /tmp/build && \
  echo "# FETCH INSTALLATION FILES ######################################" && \
  curl https://raw.githubusercontent.com/ioquake/ioq3/master/misc/linux/server_compile.sh -o /tmp/build/compile.sh && \
  curl https://ioquake3.org/data/quake3-latest-pk3s.zip --referer https://ioquake3.org/extras/patch-data/ -o /tmp/build/quake3-latest-pk3s.zip && \
  echo "# NOW THE INSTALLATION ##########################################" && \
  echo "y" | sh /tmp/build/compile.sh && \
  unzip /tmp/build/quake3-latest-pk3s.zip -d /tmp/build/ && \
  cp -r /tmp/build/quake3-latest-pk3s/* ~/ioquake3

FROM alpine:latest 
RUN adduser ioq3srv -D
COPY --from=builder /root/ioquake3 /home/ioq3srv/ioquake3
RUN ln -s /pak0.pk3 /home/ioq3srv/ioquake3/baseq3/pak0.pk3
USER ioq3srv
EXPOSE 27960/udp
ENTRYPOINT ["/home/ioq3srv/ioquake3/ioq3ded.x86_64"]

#docker build -t quake .
#export PAK0=/path/to/pak0.pk3
#docker run -it --rm -v ${PAK0}:/pak0.pk3 -p 0.0.0.0:27960:27960/udp quake3
#Tuto https://hub.docker.com/r/jberrenberg/quake3
