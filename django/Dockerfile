FROM python:3.7

ENV APP_PATH /opt/apps
WORKDIR $APP_PATH

COPY requirements.txt ./
RUN pip install --no-cache-dir -r ./requirements.txt

ARG DJANGO_PROJECT_NAME
RUN django-admin startproject $DJANGO_PROJECT_NAME .

ARG POSTGRES_PORT
ARG POSTGRES_PASSWORD
ENV POSTGRES_PORT $POSTGRES_PORT
ENV POSTGRES_PASSWORD $POSTGRES_PASSWORD

COPY local_settings.py ./${DJANGO_PROJECT_NAME}/
RUN {\
    echo 'try:'; \
    echo '    from local_settings import *'; \
    echo 'except ImportError:'; \
    echo '    pass'; \
} >> ./${DJANGO_PROJECT_NAME}/settings.py

