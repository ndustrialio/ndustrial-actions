FROM alpine:latest

RUN apk update
RUN apk add python3 python3-dev py3-pip build-base libffi-dev
RUN mkdir /github/workspace

RUN pip3 install --upgrade pip
RUN pip3 install pyyaml pygithub

COPY backstage_yml.py /github/workspace/backstage_yml.py

WORKDIR /github/workspace

ENTRYPOINT [ "python3", "backstage_yml.py", "-y" ]