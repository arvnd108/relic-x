# Owner: B
FROM python:3.11-slim AS base
ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1 PIP_NO_CACHE_DIR=1
WORKDIR /app

COPY pyproject.toml ./
COPY src ./src
RUN pip install ".[api]" && useradd --create-home --uid 1000 relicx && mkdir -p /data/storage && chown relicx /data/storage

COPY alembic.ini start.sh ./
COPY migrations ./migrations

USER relicx
EXPOSE 8000
CMD ["sh", "./start.sh"]
