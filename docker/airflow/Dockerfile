FROM apache/airflow:2.10.5

USER root

RUN groupadd -f docker && usermod -aG docker airflow

COPY requirements/airflow.txt /tmp/airflow.txt

USER airflow

RUN pip install --no-cache-dir \
  -r /tmp/airflow.txt \
  --constraint https://raw.githubusercontent.com/apache/airflow/constraints-2.10.5/constraints-3.12.txt
