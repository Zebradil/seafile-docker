FROM seafileltd/base:18.04

RUN apt update &&
    apt-get install -y \
        openjdk-8-jre \
        pwgen \
        curl \
        openssl \
        poppler-utils \
        libpython2.7 \
        libreoffice \
        libreoffice-script-provider-python \
        ttf-wqy-microhei \
        ttf-wqy-zenhei \
        xfonts-wqy \
        python-requests \
        tzdata \
        python-ceph \
        python-boto

# The S3 storage, oss storage and psd online preview etc,
# depends on the python-backages as follow:
RUN pip install \
    oss2==2.3.0 \
    psd-tools==1.4 \
    pycryptodome==3.7.2 \
    twilio==5.7.0

ENV SEAFILE_VERSION=6.3.13 SEAFILE_SERVER=seafile-pro-server

ADD seafile-pro-server_${SEAFILE_VERSION}_x86-64_Ubuntu.tar.gz /opt/seafile

COPY scripts/create_data_links.sh /etc/my_init.d/01_create_data_links.sh
COPY scripts /scripts
COPY templates /templates

EXPOSE 80

CMD ["/sbin/my_init", "--", "/scripts/start.py"]
