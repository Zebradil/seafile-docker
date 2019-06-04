# Lastet phusion baseimage as of 20180412, based on ubuntu 18.04
# See https://hub.docker.com/r/phusion/baseimage/tags/
FROM phusion/baseimage:0.11

ENV UPDATED_AT=20180412 \
    DEBIAN_FRONTEND=noninteractive

# Default command for interactive `docker run`
CMD ["/sbin/my_init", "--", "bash", "-l"]

# Utility tools
# RUN apt-get update \
#  && apt-get install --no-install-recommends -qq -y net-tools psmisc git wget curl

# Guidline for installing python libs: if a lib has C-compoment (e.g.
# python-imaging depends on libjpeg/libpng), we install it use apt-get.
# Otherwise we install it with pip.
RUN apt-get update \
 && apt-get upgrade \
 && apt-get install --no-install-recommends -y \
        python-pip \
        python-setuptools \
        python-urllib3 \
        python-ldap \
        python-mysqldb \
        zlib1g-dev \
        libmemcached-dev

COPY requirements.txt /tmp/requirements.txt
RUN pip install -U wheel \
 && pip install -r /tmp/requirements.txt

RUN rm -rf \
    /root/.cache \
    /root/.npm \
    /root/.pip \
    /usr/local/share/doc \
    /usr/share/doc \
    /usr/share/vim/vim74/doc \
    /usr/share/vim/vim74/lang \
    /usr/share/vim/vim74/spell/en* \
    /usr/share/vim/vim74/tutor \
    /var/lib/apt/lists/* \
    /tmp/*

WORKDIR /opt/seafile
