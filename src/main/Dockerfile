FROM python:3.12-slim

LABEL maintainer="github/dev-yusupov"

ENV PYTHONUNBUFFERED 1

# Set the working directory in the container
RUN mkdir /app
WORKDIR /app

COPY ./requirements.txt /app/requirements.txt

# Install system dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        postgresql-client \
        libpq-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install the dependencies
RUN python3 -m venv /.venv/ && \
    /.venv/bin/pip install --upgrade pip && \
    /.venv/bin/pip install -r requirements.txt \
    && adduser --disabled-password --no-create-home django-user

# Copy the content of the local src directory to the working directory
COPY ./app /app/
RUN ls -la /app

RUN echo Main Service is running on http://localhost:9000

ENV PATH="/.venv/bin/:$PATH"

# Command to run on container start
CMD ["bash", "-c", "source /.venv/bin/activate && python3 manage.py runserver 0.0.0.0:9000"]
