FROM python:3.10-slim-buster

ENV POETRY_VERSION=1.2.0 \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PIP_DEFAULT_TIMEOUT=100

WORKDIR /app

RUN apt-get update 
RUN pip install wheel
RUN pip install -U pip setuptools \
    && pip install poetry==${POETRY_VERSION}

COPY ./pyproject.toml ./

RUN poetry install 

COPY . .

EXPOSE 8000
ENV FLASK_APP=api-flask.main
CMD ["poetry", "run","flask", "run", "--host=0.0.0.0", "--port=8000"]