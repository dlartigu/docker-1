FROM debian:latest

RUN apt-get update
RUN apt-get check
RUN apt-get upgrade -y

RUN apt-get install -y apache2

COPY index.html /var/www/html/

EXPOSE 80

#docker build -t htmlsrvr .
#docker run -it -p 8585:80 htmlsrvr
#service apache2 restart