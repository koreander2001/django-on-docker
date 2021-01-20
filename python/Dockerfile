FROM python:3.9-buster

RUN mkdir /code
WORKDIR /code

ADD requirements.txt /code/

RUN pip install --upgrade pip &&\
    pip install -r requirements.txt

ADD . /code/

