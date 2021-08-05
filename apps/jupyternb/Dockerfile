FROM arm64v8/ubuntu:latest
RUN apt-get update && apt-get -y update
RUN apt-get install -y build-essential python3.6 python3-pip python3-dev
RUN pip3 -q install pip --upgrade

RUN mkdir src
WORKDIR src/
COPY . .

RUN pip3 install pandas matplotlib numpy
RUN pip3 install jupyter

WORKDIR /src/notebooks

RUN mkdir /data
VOLUME ["/data"]
ENV JUPYTER_DATA_DIR=/data

# Add Tini. Tini operates as a process subreaper for jupyter. This prevents kernel crashes.
ENV TINI_VERSION v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-arm64 /tini
RUN chmod +x /tini
ENTRYPOINT ["/tini", "--"]

EXPOSE 8888

CMD ["jupyter", "notebook", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]


