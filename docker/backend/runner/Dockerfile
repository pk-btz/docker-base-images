FROM python:3.9.16-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
    libpq5 \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

RUN groupadd --gid 1001 appuser \
    && useradd --uid 1001 --gid 1001 --create-home appuser

USER 1001
WORKDIR /home/appuser/app

COPY --from=ghcr.io/pk-btz/devbase-backend-builder --chown=1001:1001 /home/appuser/app/ .

ENV PATH="/home/appuser/app/venv/bin:$PATH"