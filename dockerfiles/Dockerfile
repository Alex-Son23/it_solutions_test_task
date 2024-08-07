FROM python:3.11.3-slim as python-base

ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    \
    PIP_NO_CACHE_DIR=off \
    PIP_DISABLE_PIP_VERSION_CHECK=on \
    PIP_DEFAULT_TIMEOUT=100 \
    POETRY_VERSION=1.8.2 \
    POETRY_HOME="/opt/poetry" \
    POETRY_VIRTUALENVS_IN_PROJECT=true \
    POETRY_NO_INTERACTION=1 \
    PYSETUP_PATH="/opt/pysetup" \
    VENV_PATH="/opt/pysetup/.venv"

ENV PATH="$POETRY_HOME/bin:$VENV_PATH/bin:$PATH"

FROM python-base as builder
LABEL stage="builder"
RUN apt-get update && \
    apt-get install --no-install-recommends -y curl build-essential


RUN curl -sSL https://install.python-poetry.org | python3 -

WORKDIR $PYSETUP_PATH

COPY poetry.lock pyproject.toml ./


RUN poetry install

FROM python-base as development
WORKDIR $PYSETUP_PATH
COPY --from=builder $PYSETUP_PATH $PYSETUP_PATH
COPY src /test_task-api/
WORKDIR /test_task-api
EXPOSE 8000
