#
#  Author: Guido Schmutz
#  Date: 2020-07-27
#
#  https://github.com/trivadispf/docker-presto-cli
#
FROM alpine:latest

ENV DEBIAN_FRONTEND noninteractive

ENV PRESTODB_VERSION=0.238.1 \
    PRESTODB_CLI_HOME=/opt/presto-cli \
    PRESTODB_CLI_JAR=/opt/presto-cli/presto-cli-${PRESTODB_VERSION}-executable.jar

# Install Java
RUN apk --no-cache add openjdk11 --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community

# Install PrestoDB CLI
RUN mkdir -p "/opt/presto-cli" \
 && wget "https://repo1.maven.org/maven2/io/com/facebook/presto/presto-cli/${PRESTODB_VERSION}/presto-cli-${PRESTODB_VERSION}-executable.jar" \
      -q -O "$PRESTODB_CLI_JAR" \
 && chmod +x "$PRESTODB_CLI_JAR" \
 && ln -s "$PRESTODB_CLI_JAR" /usr/local/bin/presto \
 && apk update \
 && apk add less \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["presto"]

