FROM alpine:latest

RUN apk update
RUN apk add python3 python3-dev py3-pip build-base libffi-dev
RUN mkdir app

RUN pip3 install --upgrade pip
RUN pip3 install pyyaml pygithub

COPY backstage_yml.py /backstage_yml.py

ENTRYPOINT [ "python3", "backstage_yml.py", "-y" ]