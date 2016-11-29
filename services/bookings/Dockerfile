FROM ubuntu:14.04

MAINTAINER Tanuj Gupta "tanuj.genx@gmail.com"

RUN apt-get update
RUN apt-get install -y --force-yes python python-dev python-setuptools software-properties-common gcc python-pip supervisor
RUN apt-get clean all

RUN pip install Flask==0.11.1

COPY bookings.py /opt/service/bookings.py

# Cope supervisor config to start the service automatically
COPY service.ini /etc/supervisor/supervisor.d/service.ini

#Create your logging directory if you are not sure its already created
RUN mkdir -p /var/log/bookings

# Flask Port
EXPOSE 5000

# Stop supervisord if already running]
CMD ["service","supervisor","reload"]

