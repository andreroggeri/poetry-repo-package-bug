FROM public.ecr.aws/docker/library/python:3.8.18-slim as base-image

ENV PATH=/root/.local/bin:${PATH}

RUN apt-get update \
    && apt-get install -y curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

RUN curl -sSL https://install.python-poetry.org | python3

RUN poetry --version

RUN poetry config --list

RUN python -m sysconfig

COPY pyproject.toml poetry.lock ./

# Workaround
# ENV POETRY_INSTALLER_PARALLEL=0

RUN poetry install -vvv --no-dev --no-root