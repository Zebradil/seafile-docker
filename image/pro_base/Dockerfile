FROM seafileltd/base:18.04

# syslog-ng and syslog-forwarder would mess up the container stdout, not good
# when debugging/upgrading.

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
