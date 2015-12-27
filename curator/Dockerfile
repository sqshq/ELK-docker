FROM alpine:3.2

RUN apk --update add python py-pip && \
    pip install elasticsearch-curator==3.4.0

# add tasks scripts
ADD ./tasks /etc/periodic/daily
RUN chmod a+x /etc/periodic/daily/*

CMD ["crond", "-f", "-l", "8"]
