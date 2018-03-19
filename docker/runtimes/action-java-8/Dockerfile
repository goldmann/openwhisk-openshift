FROM jboss/base-jdk:8

USER root

COPY proxy /opt/jboss/javaAction
RUN  chown jboss:jboss -R /opt/jboss/javaAction \
  # OpenShift compatibility
  && chgrp -R 0 /opt/jboss \
  && chmod -R g+rwX /opt/jboss

USER 1000

RUN cd /opt/jboss/javaAction \
  # Build the jar
  && ./gradlew oneJar \
  # Copy built jar to home directory
  && mv /opt/jboss/javaAction/build/libs/javaAction-all.jar /opt/jboss/javaAction-all.jar \
  # Clean up
  && rm -rf /opt/jboss/javaAction /opt/jboss/.gradle

CMD ["java", "-jar", "/opt/jboss/javaAction-all.jar"]
