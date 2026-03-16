FROM python:3.12-slim

RUN apt-get update && apt-get install -y git && rm -rf /var/lib/apt/lists/*

COPY requirements /tmp/requirements
RUN pip install --no-cache-dir -r /tmp/requirements/dbt.txt

WORKDIR /dbt

COPY dbt/packages.yml ./packages.yml
COPY dbt/dbt_project.yml ./dbt_project.yml

RUN dbt deps
