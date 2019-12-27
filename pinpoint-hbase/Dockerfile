FROM java:8-jdk

COPY hbase-1.2.6.1-bin.tar.gz /
COPY hbase-site.xml /
COPY hbase-create.hbase /

RUN cd / && ls \
    && tar zxvf /hbase-1.2.6.1-bin.tar.gz -C /usr/local/ \
    && mv /hbase-site.xml /usr/local/hbase-1.2.6.1/conf/ \
    && /usr/local/hbase-1.2.6.1/bin/start-hbase.sh \
    && sleep 10 \
    && /usr/local/hbase-1.2.6.1/bin/hbase shell /hbase-create.hbase \
    && /usr/local/hbase-1.2.6.1/bin/stop-hbase.sh \
    && rm -rf /hbase-create.hbase \
    && rm -rf /hbase-1.2.6.1-bin.tar.gz

ENTRYPOINT /usr/local/hbase-1.2.6.1/bin/hbase master start
