FROM python:3.9.16 AS builder

ENV DEBIAN_FRONTEND=noninteractive
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

RUN groupadd --gid 1001 appuser \
    && useradd --uid 1001 --gid 1001 --create-home appuser \
    apt update && apt upgrade -y
USER appuser

WORKDIR /home/appuser/app

COPY --chown=appuser:appuser requirements.txt ./

RUN python -m venv venv
RUN . venv/bin/activate && pip install -r requirements.txt --no-cache-dir
