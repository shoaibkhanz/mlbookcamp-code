FROM python:3.8.13-buster

ENV PYTHONUNBUFFERED=TRUE

RUN pip install -U pip
RUN pip install poetry

WORKDIR /app

COPY [ "pyproject.toml", "poetry.lock", "./" ]
COPY ["*.py", "churn-model.bin", "./"]

RUN poetry config virtualenvs.create false
RUN poetry install --no-interaction

EXPOSE 9696

ENTRYPOINT ["gunicorn", "--bind", "0.0.0.0:9696", "churn_serving:app"]

