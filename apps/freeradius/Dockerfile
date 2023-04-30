FROM arm64v8/debian

RUN apt-get update && \
    apt-get -o Apt::Install-Recommends=0 install -y freeradius build-essential git && \
    git clone https://github.com/Yelp/dumb-init.git /dumb-init && \
    cd /dumb-init && \
    make && \
    cp dumb-init /sbin/dumb-init && \
    cd / && \
    rm -rf /dumb-init && \
    apt-get remove --purge -y build-essential git && \
    apt-get --purge -y autoremove && \
    rm -rf /var/lib/apt/lists/*
#    rm -rf /etc/freeradius/*

COPY eap /etc/freeradius/3.0/mods-available

EXPOSE 1812/udp
EXPOSE 1813/udp

VOLUME /etc/freeradius/3.0

ENTRYPOINT ["/sbin/dumb-init"]
CMD ["/usr/sbin/freeradius", "-f", "-d", "/etc/freeradius/3.0", "-X"]
