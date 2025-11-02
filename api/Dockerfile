FROM python:3.11-bookworm

WORKDIR /app
COPY . .

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && apt-get install -y \
    python3-libtorrent ffmpeg gcc libpq-dev rsync handbrake handbrake-cli \
    && rm -rf /var/lib/apt/lists/*

ENV PYTHONPATH="/usr/lib/python3/dist-packages:$PYTHONPATH"

RUN pip install --no-cache-dir -r requirements.txt

CMD ["bash", "-c", "chmod +x /app/entrypoint.sh && /app/entrypoint.sh"]
