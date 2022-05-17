FROM alpine:latest

RUN apk update
RUN apk add python3 python3-dev py3-pip build-base libffi-dev
RUN mkdir app

RUN pip3 install --upgrade pip
RUN pip3 install pyyaml pygithub

COPY backstage_yml.py app/backstage_yml.py

WORKDIR app

ENTRYPOINT [ "python3", "app/backstage_yml.py", "-y" ]