FROM python:3.10-alpine AS builder
WORKDIR /src

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .
CMD ["python3", "server.py"]

FROM builder as dev-envs

RUN apk update
RUN apk add git
RUN addgroup -S docker
RUN adduser -S --shell /bin/bash --ingroup docker vscode
