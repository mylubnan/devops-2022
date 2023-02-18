FROM continuumio/anaconda3

WORKDIR /

RUN apt-get update && apt-get install -y git postgresql  postgresql-contrib wget gnupg2 sudo nano

RUN conda install -y numpy pandas jupyter ipython psycopg2 pyspark

RUN pip install findspark

RUN echo "deb http://www.apache.org/dist/cassandra/debian 311x main" | tee -a /etc/apt/sources.list.d/cassandra.sources.list
RUN wget -q -O- https://www.apache.org/dist/cassandra/KEYS | apt-key add -

RUN apt-get update && apt-get install -y cassandra
RUN pip install cassandra-driver

RUN pip install apache-airflow

RUN wget -qO - https://downloads.apache.org/kafka/3.4.0/kafka-3.4.0-src.tgz | tar -xzf - -C /opt && \
    mv /opt/kafka-3.4.0-src /opt/kafka

ENV PATH="/opt/kafka/bin:${PATH}"

RUN pip install kafka-python

COPY . .

CMD ["/bin/bash"]