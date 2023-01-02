FROM adoptopenjdk/openjdk11:ubuntu-jre

ENV FC_LANG en-US LC_CTYPE en_US.UTF-8

# setup
RUN rm -rf /var/lib/{apt,dpkg,cache,log}/ && \
    mkdir -p /plugins && chmod a+rwx /plugins && \
    useradd --shell /bin/bash metabase

USER metabase
WORKDIR /app

# copy app from the offical image
COPY --from=metabase/metabase:v0.45.1 /app /app
ADD config.yml .
# expose our default runtime port
EXPOSE 3000

# run it
ENTRYPOINT ["/app/run_metabase.sh"]