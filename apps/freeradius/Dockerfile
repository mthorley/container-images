FROM arm64v8/ubuntu:latest
RUN apt-get update && apt-get -y update

RUN install -d -o root -g root -m 0755 /etc/apt/keyrings
RUN curl -s 'https://packages.networkradius.com/pgp/packages%40networkradius.com' | \
    tee /etc/apt/keyrings/packages.networkradius.com.asc > /dev/null

RUN echo "deb [signed-by=/etc/apt/keyrings/packages.networkradius.com.asc] http://packages.networkradius.com/freeradius-3.2/ubuntu/jammy jammy main" | \
    tee /etc/apt/sources.list.d/networkradius.list > /dev/null

RUN apt-get install -y freeradius

EXPOSE 1812/udp 1813/udp

CMD ["radiusd", "-X"]
