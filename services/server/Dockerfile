# base image
FROM python:3.9.4-slim

# install netcat
RUN apt-get update && \
    apt-get -y install netcat && \
    apt-get clean

# set working directory
WORKDIR /usr/src/app

# add and install requirements
COPY ./requirements.txt /usr/src/app/requirements.txt
RUN pip install -r requirements.txt

ENV FLASK_ENV="development"
ENV APP_SETTINGS="project.config.DevelopmentConfig"
ENV POSTGRES_USER="postgres"
ENV POSTGRES_PASSWORD="securepassword"
ENV POSTGRES_SERVICE="postgres-postgresql"

# add entrypoint.sh
COPY ./entrypoint.sh /usr/src/app/entrypoint.sh
RUN chmod +x /usr/src/app/entrypoint.sh

# add app
COPY . /usr/src/app

# run server
CMD ["./entrypoint.sh"]
