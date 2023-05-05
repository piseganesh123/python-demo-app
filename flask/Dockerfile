#FROM --platform=$BUILDPLATFORM python:3.10-alpine AS builder

#WORKDIR /src
#COPY requirements.txt /src
#RUN --mount=type=cache,target=/root/.cache/pip \
#    pip3 install -r requirements.txt

#COPY . .

#CMD ["python3", "server.py"]

#FROM builder as dev-envs

#RUN <<EOF
#apk update
#apk add git
#EOF

#RUN <<EOF
#addgroup -S docker
#adduser -S --shell /bin/bash --ingroup docker vscode
#EOF

# install Docker tools (cli, buildx, compose)
#COPY --from=gloursdocker/docker / /

#CMD ["python3", "server.py"]

FROM python:3.10-alpine AS builder
#FROM python:3.8-slim-buster

WORKDIR /src

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .
CMD ["python3", "server.py"]
#CMD ["python3", "-m" , "flask", "run", "--host=0.0.0.0"]

FROM builder as dev-envs

RUN apk update
RUN apk add git

RUN addgroup -S docker
RUN adduser -S --shell /bin/bash --ingroup docker vscode