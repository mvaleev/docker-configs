FROM python:2.7.13-alpine

ENV ELASTICSEARCH_HOST elasticsearch
ENV ELASTICSEARCH_PORT 9200
ENV ELASTALERT_CONFIG /opt/elastalert/config/elastalert.yaml

COPY ./start-elastalert.sh /opt/

RUN chmod +x /opt/start-elastalert.sh; \
    apk add --update python-dev gcc musl-dev build-base libffi-dev openssl-dev git; \
    git clone https://github.com/Yelp/elastalert.git /opt/elastalert; \
    cd /opt/elastalert; \
    python setup.py install; \
    pip install -r requirements.txt; \
    apk del python-dev gcc musl-dev build-base libffi-dev openssl-dev

WORKDIR /opt/elastalert

CMD ["/opt/start-elastalert.sh"]
