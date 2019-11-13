FROM python:2

WORKDIR /code

RUN apt-get update && \
    apt-get install -y git && \
    apt-get install -y wget

RUN pip install pika==0.12.0
RUN pip install numpy

RUN wget "https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh"
RUN chmod +x wait-for-it.sh

RUN git clone https://github.com/Emmanuel93/api-master.git --branch fashion_docker --single-branch

ENV RUN_SCRIPT_PATH api-master/optimizacion/algoritmogenetico/
ENV RUN_SCRIPT CGA.py

ENTRYPOINT ./wait-for-it.sh broker:5672 -t 30 && cd $RUN_SCRIPT_PATH && python $RUN_SCRIPT
