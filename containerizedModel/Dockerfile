FROM frolvlad/alpine-python-machinelearning
MAINTAINER Hilton Pintor

#set envionment variables
# ENV PYTHONUNBUFFERED 1

# run this before copying requirements for cache efficiency
RUN pip install --upgrade pip

#set work directory early so remaining paths can be relative
WORKDIR /app

# Adding requirements file to current directory
# just this file first to cache the pip install step when code changes
COPY requirements.txt .

#install dependencies
# RUN apk add --update --no-cache g++ gcc libxslt-dev
RUN pip install -r requirements.txt
# RUN apk add --update --no-cache --virtual .build-deps \
# 		gcc \
#         g++ \
#         python3-dev \
#         python-libxml \
#         libxml2 \
#         libxml2-dev && \
#     apk add libxslt-dev && \
#     pip install --no-cache-dir -r requirements.txt && \
#     apk del .build-deps

# copy code itself from context to image
COPY . .

# run from working directory, and separate args in the json syntax
# CMD ["python", "./manage.py", "runserver", "0.0.0.0:8000"]