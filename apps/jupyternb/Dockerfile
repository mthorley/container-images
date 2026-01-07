
# Use a specific Ubuntu LTS version for stability and security
FROM arm64v8/ubuntu:22.04

# Install dependencies and clean up apt cache to reduce vulnerabilities
RUN apt-get update && \
	apt-get install -y --no-install-recommends \
		build-essential \
		python3.10 \
		python3-pip \
		python3-dev \
		ca-certificates \
		wget && \
	rm -rf /var/lib/apt/lists/*

# Upgrade pip securely
RUN python3.10 -m pip install --upgrade pip

# Create working directory
RUN mkdir /src
WORKDIR /src
COPY . .

# Install Python packages with pinned versions to reduce vulnerabilities
RUN pip install --no-cache-dir pandas==2.2.0 matplotlib==3.8.2 numpy==1.26.4 jupyter==1.0.0

WORKDIR /src/notebooks

# Data directory setup
RUN mkdir /data
VOLUME ["/data"]
ENV JUPYTER_DATA_DIR=/data

# Add Tini and verify checksum for security
ENV TINI_VERSION v0.19.0
ENV TINI_SHA256 07952557df20bfd2a95f9bef198b445e006171969499a1d361bd9e6f8e5e0e81
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini-arm64 /tini
RUN echo "$TINI_SHA256  /tini" | sha256sum -c - && chmod +x /tini
ENTRYPOINT ["/tini", "--"]

EXPOSE 8888

CMD ["jupyter", "notebook", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]
#        "--certfile=/etc/ssl/private/tls.crt", "--keyfile=/etc/ssl/private/tls.key"]
