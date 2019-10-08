FROM ubuntu:16.04

ENV LAST_UPDATED_AT 2018-05-21

RUN apt-get update \
    && apt-get install --no-install-recommends -y \
	lib32gcc1 \
	lib32stdc++6 \
	ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /steamcmd 
WORKDIR /steamcmd
ADD https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz steamcmd_linux.tar.gz
RUN tar -zxvf steamcmd_linux.tar.gz


RUN ./steamcmd.sh +login anonymous +force_install_dir /csgo +app_update 740 validate +quit

COPY containerfs /

RUN mkdir /root/.steam/sdk32
RUN ln -s /steamcmd/linux32/steamclient.so /root/.steam/sdk32/steamclient.so

WORKDIR /csgo

CMD ["./start.sh"]

#docker build -t csgo-server .
#docker run \
#   -d \
#    -p 27015:27015/tcp \
#    -p 27015:27015/udp \
#    -p 27020:27020/udp \
#    -p 27020:27020/tcp \
#    -e "SERVER_HOSTNAME=hostname" \
#    -e "SERVER_PASSWORD=password" \
#    -e "RCON_PASSWORD=rconpassword" \
#    -e "STEAM_ACCOUNT=gamelogintoken" \
#    csgo-server