# pull official base image
FROM python:3.8.3-alpine

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apk update && apk upgrade \
    && apk add postgresql-client \
        postgresql-dev \
        musl-dev \
        gcc \
        linux-headers \
        gettext-dev \
    && pip install pipenv

# install dependencies
RUN pip install --upgrade pip
COPY ./requirements/base.txt .
COPY ./requirements/testing.txt .
COPY ./requirements/development.txt .

RUN pip install -r development.txt

# copy project
COPY . .

ENTRYPOINT ["/usr/src/app/docker/entrypoint.sh"]