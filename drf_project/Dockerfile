FROM python:3.10.1-slim-buster

# set working directory
WORKDIR /usr/src/app

# set environment variables
ENV SECRET_KEY 'django-insecure-ruoqx5tb)1%a6(#jf+rh-pez!+s#z7e64$q@kery(r=vyrf#*8'

# install system dependencies
RUN apt-get update \
  && apt-get -y install gcc postgresql netcat-openbsd\
  && apt-get clean

# add and install requirements
RUN pip install --upgrade pip
RUN ls
COPY ./drf_project/requirements.txt .
RUN pip install -r requirements.txt

# add app
COPY . .


# run gunicorn


ENTRYPOINT gunicorn --workers 2 drf_project.drf_project.wsgi:application