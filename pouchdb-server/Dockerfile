#
# PouchDB Server Dockerfile
# VERSION 1.1.1
#

# Pull Nodejs-Runtime stable base image
FROM appelgriebsch/nodejs-runtime:stable
MAINTAINER Andreas Gerlach <info@appelgriebsch.com>
LABEL AUTHOR="Andreas Gerlach <info@appelgriebsch.com>"
LABEL NAME="pouchdb-server"
LABEL VERSION="1.1.1"

# define the network segment it is bind to
ENV POUCHDB_BIND    127.0.0.1
# define port the service is exposed to
ENV POUCHDB_PORT    5984
# define the pouchdb database driver (leveldown or sqlite)
ENV POUCHDB_DRIVER  leveldown

USER root
RUN   mkdir -p /data/pouchdb && \
      chown -R nobody:nobody /data/pouchdb && \
      chown -R nobody:nobody $NODEJS_APPDIR

ADD start_instance.sh /tmp/

RUN chmod 755 /tmp/start_instance.sh

# Define mountable directories.
VOLUME /data/pouchdb

# Expose ports.
EXPOSE $POUCHDB_PORT

# run service
USER nobody
ENTRYPOINT ["/tmp/start_instance.sh"]
