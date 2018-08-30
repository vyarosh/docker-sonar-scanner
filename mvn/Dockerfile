FROM openjdk:8-jdk

ARG MAVEN_VERSION=3.5.4
ARG USER_HOME_DIR="/root"
ARG SHA=ce50b1c91364cb77efe3776f756a6d92b76d9038b0a0782f7d53acf1e997a14d
ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries

RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
  && echo "${SHA}  /tmp/apache-maven.tar.gz" | sha256sum -c - \
  && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG "$USER_HOME_DIR/.m2"

RUN curl -SL https://raw.githubusercontent.com/carlossg/docker-maven/f581ea002e5d067deb6213c00a4d217297cad469/jdk-8/mvn-entrypoint.sh --output /usr/local/bin/mvn-entrypoint.sh
RUN curl -SL https://raw.githubusercontent.com/carlossg/docker-maven/f581ea002e5d067deb6213c00a4d217297cad469/jdk-8/settings-docker.xml --output /usr/share/maven/ref/settings-docker.xml

ENTRYPOINT ["/usr/local/bin/mvn-entrypoint.sh"]
CMD ["mvn", "sonar:sonar", "-f", "/project/pom.xml"]