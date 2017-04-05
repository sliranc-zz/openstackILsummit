FROM ubuntu:14.04

RUN apt-get update &&\
    apt-get install ubuntu-cloud-keyring &&\
    echo "deb http://ubuntu-cloud.archive.canonical.com/ubuntu"\
         "trusty-updates/kilo main" > /etc/apt/sources.list.d/cloudarchive-kilo.list &&\
    apt-get update && apt-get install python-pip python-dev supervisor \
          openstack-dashboard apache2 libapache2-mod-wsgi -y &&\
    apt-get remove openstack-dashboard-ubuntu-theme -y
RUN mkdir -p /var/log/horizon && chown horizon /var/log/horizon

ADD local_settings.py /etc/openstack-dashboard/local_settings.py

EXPOSE 80
CMD ["/bin/bash" , "-c" , "source /etc/apache2/envvars &&  /usr/sbin/apache2 -DFOREGROUND"]
