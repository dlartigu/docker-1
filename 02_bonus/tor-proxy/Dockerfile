FROM alpine:edge

RUN apk update
RUN apk add tor

RUN echo "Log notice stdout" >> /etc/torrc
RUN echo "SocksPort 0.0.0.0:9150" >> /etc/torrc

EXPOSE 9150

CMD tor -f /etc/torrc

#docker build -t tor -f Dockerfile .
#docker run -d --rm --name tor -p 9150:9150 tor
#Tuto https://dev.to/boris/running-tor-using-docker-4d7h
#After that, you'll have a tor proxy running in your 127.0.0.1:9150 so go ahead and configure your browser of choice to use a SOCKS proxy on 127.0.0.1:9150 and you'll go from this: