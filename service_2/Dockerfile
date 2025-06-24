FROM ghcr.io/astral-sh/uv:python3.12-alpine
#installing curl for healthcheck not in image
RUN apk add --no-cache curl

WORKDIR /app

COPY pyproject.toml uv.lock ./
RUN uv sync --no-dev --no-install-project

COPY app.py ./

EXPOSE 8002

CMD ["uv", "run", "app.py"]
