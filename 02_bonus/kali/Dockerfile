FROM kalilinux/kali-linux-docker

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -y update && apt-get -y dist-upgrade && apt-get -y autoremove && apt-get clean

RUN apt-get -y install kali-linux-top10 exploitdb man-db dirb nikto wpscan uniscan


RUN service postgresql start && msfdb init && service postgresql stop

VOLUME /root /var/lib/postgresql

EXPOSE 4444

WORKDIR /root
CMD ["/bin/bash"]

#docker build -t kali .
#docker run -it kali