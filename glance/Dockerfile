# Glance
#
# VERSION               1.0
FROM ubuntu:latest
MAINTAINER Jorge Munoz "jorge.munoz@rackspace.com"

#Update sources
RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update

#Install Git and build dependencies:
RUN apt-get install -y git
RUN apt-get install -y python-dev libxml2-dev libxslt1-dev libsasl2-dev libsqlite3-dev libssl-dev libldap2-dev vim sheepdog curl

RUN apt-get install -y python-pip
RUN pip install pbr

#Clone Glance’s trunk branch from GitHub:
RUN git clone git://github.com/openstack/glance

#Set working Directory
WORKDIR /glance

#Install Glance and setup:
RUN python setup.py install
RUN mkdir -p /var/log/glance 
RUN touch /var/log/glance/api.log

#Ports
EXPOSE 35357 9292 9191 5672 5672 7000

#Run Glance
CMD glance-api --config-file /glance/etc/glance-api.conf
