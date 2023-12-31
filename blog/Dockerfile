# MAINTAINER        Gevin <flyhigher139@gmail.com>
# DOCKER-VERSION    1.6.2
#
# Dockerizing Ubuntu: Dockerfile for building Ubuntu images


FROM       ubuntu:14.04
MAINTAINER Gevin <flyhigher139@gmail.com>

# COPY sources.list /etc/apt/sources.list
RUN apt-get update && apt-get install -y vim && \
    apt-get install -y nginx python-dev python-pip libpq-dev postgresql-client && \
    apt-get clean all


RUN echo "daemon off;" >> /etc/nginx/nginx.conf

# COPY pip.conf /root/.pip/pip.conf 
RUN pip install supervisor uwsgi

COPY supervisord.conf /etc/supervisord.conf

RUN mkdir -p /etc/supervisor.conf.d && \
    mkdir -p /var/log/supervisor

RUN mkdir -p /usr/src/app && mkdir -p /var/log/uwsgi
WORKDIR /usr/src/app

COPY requirements.txt /usr/src/app/requirements.txt
RUN pip install -r /usr/src/app/requirements.txt

COPY . /usr/src/app

RUN ln -s /usr/src/app/mayblog_nginx.conf /etc/nginx/sites-enabled


RUN /usr/bin/python2.7 manage.py collectstatic --noinput


EXPOSE 8000


CMD ["/bin/bash", "/usr/src/app/init.sh"]
