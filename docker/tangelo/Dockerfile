FROM jreeme/tangelo:0.9

RUN pip install pykafka tika
RUN pip install urllib3 -U
RUN mkdir /tmp/src && cd /tmp/src && git clone https://github.com/sotera/Datawake
RUN cd /usr/local/share/tangelo/web && rm -rf *
RUN cd /usr/local/share/tangelo/web && cp -R /tmp/src/Datawake/server/datawake/ .
RUN cd /usr/local/share/tangelo/web && cp -R /tmp/src/Datawake/server/forensic/ .
RUN cd /tmp/src && rm -rf *

ENV DW_DB=memex_sotera DW_DB_USER=root DW_DB_PASSWORD=root \
TCP_PORT=3306 DW_MOCK_AUTH=1 DW_MOCK_FORENSIC_AUTH=1 DW_CONN_TYPE=mysql \
MITIE_HOME=/usr/lib/mitie/MITIE PYTHONPATH=/usr/local/share/tangelo/web:/home/datawake/src/Datawake/server:$PYTHONPATH \
FORENSIC_ES_URL=els.istresearch.com:9200 FORENSIC_ES_INDEX=memex_ht \
FORENSIC_ES_MRPN=10 DEEPDIVE_URL=https://api.clearcutcorp.com/docs DEEPDIVE_USER=justin DEEPDIVE_REPO=atf \
DEEPDIVE_TOKEN=cac59b455cbdedc4c54d767c254b6cea2d8267da DIG_URL=http://none.com DW_CRAWL=True DW_EXTERNAL_LINK_NAMES=Tellfinder \
DW_EXTERNAL_LINK_VALUES=https://tellfinder.istresearch.com:8443/tellfinder/entitylist.jsp?tip\=$VALUE&attibute\=false

COPY tangelo.conf /etc/tangelo.conf
