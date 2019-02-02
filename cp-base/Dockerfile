FROM centos:7.6.1810
RUN mkdir /kafka && mkdir -p /etc/confluent/docker
COPY files/. /kafka/.
RUN cp /kafka/*.repo /etc/yum.repos.d/ \
    && yum update -y \
    && yum install java-1.8.0-openjdk-headless.x86_64 nc python wget -y \
    && rpm --import /kafka/archive.key \
    && cd /kafka \
    && python pip-19.0.1-py2.py3-none-any.whl/pip install pip-19.0.1-py2.py3-none-any.whl \
    && pip install setuptools* \
    && pip install websocket_client* \
    && pip install requests* \
    && pip install PyYAML* \
    && pip install enum* \
    && pip install texttable-0* \
    && pip install docopt* \
    && pip install func* \
    && pip install jsonschema* \
    && pip install cached* \
    && pip install docker* \
    && pip install MarkupSafe*.tar.gz \
    && pip install Jinja* \
    && pip install pbr* \
    && pip install mock* \
    && pip install confluent*.zip \
    && yum clean all \
    && rm -rf /var/cache/yum \
    && cp -r misc/. /etc/confluent/. \
    && cp -r python-package/confluent/. /usr/lib/python2.7/site-packages/confluent/. \
    && rm -rf /kafka
#COPY files/misc/docker/. /etc/confluent/docker/.
#COPY files/python-package/confluent/. /usr/lib/python2.7/site-packages/confluent/.
ENV CUB_CLASSPATH=/etc/confluent/docker/docker-utils.jar

