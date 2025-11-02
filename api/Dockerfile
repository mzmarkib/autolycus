FROM python:3.10-buster
WORKDIR /app
COPY . .

# System dependencies for Python packages
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y && \
    apt-get install -y \
    python3-libtorrent \
    ffmpeg \
    gcc \
    libpq-dev \
    rsync \
    handbrake-cli \
    libxml2-dev \
    libxslt1-dev \
    zlib1g-dev \
    libffi-dev \
    libssl-dev \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Ensure Python paths and install dependencies
ENV PYTHONPATH="/usr/lib/python3/dist-packages:$PYTHONPATH"

# (Optional) Patch libtorrent version if needed
RUN sed -i 's/libtorrent==2.0.7/libtorrent==2.0.11/' requirements.txt || true

RUN pip install --upgrade pip setuptools wheel && \
    pip install --no-cache-dir -r requirements.txt

CMD ["bash", "-c", "chmod +x /app/entrypoint.sh && /app/entrypoint.sh"]