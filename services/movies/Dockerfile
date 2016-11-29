FROM ubuntu:14.04

MAINTAINER Tanuj Gupta "tanuj.genx@gmail.com"

RUN apt-get update
RUN apt-get install -y --force-yes python python-dev python-setuptools software-properties-common gcc python-pip supervisor
RUN apt-get clean all

RUN pip install Flask==0.11.1

COPY movies.py /opt/service/movies.py
COPY db /opt/service/db

# Copy supervisor config to start the service automatically
COPY supervisord.conf /etc/supervisor/supervisord.conf
COPY service.conf /etc/supervisor/conf.d/service.conf

# Create your logging directory if you are not sure its already created
RUN mkdir -p /var/log/movies
RUN mkdir -p /var/log/supervisor

# Flask Port
EXPOSE 5001

# Start suypervisor service
CMD ["/usr/bin/supervisord"]

