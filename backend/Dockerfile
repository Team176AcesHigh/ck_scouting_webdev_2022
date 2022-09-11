FROM python:3.9.14-alpine3.16

RUN mkdir /app
WORKDIR /app
RUN pip install gunicorn

RUN apk add libpq-dev mysql-dev build-base

COPY ./requirements.txt ./requirements.txt
RUN pip install -r ./requirements.txt

COPY . .

CMD gunicorn --bind 0.0.0.0:${LISTEN_PORT:-5000} wsgi:app