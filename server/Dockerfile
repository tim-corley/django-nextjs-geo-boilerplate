#---- Base python ----
FROM python:3.9-slim-bullseye as base

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

# Install system packages
RUN apt-get update &&\
    apt-get install -y binutils libproj-dev gdal-bin &&\
    apt-get install -y libgeos++-dev libgeos-c1v5 libgeos-dev libgeos-doc

# Create app directory & install requirements
WORKDIR /src
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt 

# ---- Copy Files/Build ----
FROM base

WORKDIR /src

COPY . /src

RUN chmod -R 777 /src
