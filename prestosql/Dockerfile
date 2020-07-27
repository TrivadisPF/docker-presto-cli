#
#  Author: Guido Schmutz
#  Date: 2020-07-27
#
#  https://github.com/trivadispf/docker-presto-cli
#
FROM alpine:latest

ENV DEBIAN_FRONTEND noninteractive

ENV PRESTOSQL_VERSION=339 \
    PRESTOSQL_CLI_HOME=/opt/presto-cli \
    PRESTOSQL_CLI_JAR=/opt/presto-cli/presto-cli-${PRESTOSQL_VERSION}-executable.jar

# Install PrestoSQL CLI
RUN mkdir -p "/opt/presto-cli" \
 && wget "https://repo1.maven.org/maven2/io/prestosql/presto-cli/${PRESTOSQL_VERSION}/presto-cli-${PRESTOSQL_VERSION}-executable.jar" \
      -q -O "$PRESTOSQL_CLI_JAR" \
 && chmod +x "$PRESTOSQL_CLI_JAR" \
 && ln -s "$PRESTOSQL_CLI_JAR" /usr/local/bin/presto \
 && apk update \
 && apk add less \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["presto"]