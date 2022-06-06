# https://hub.docker.com/orgs/seataio
FROM openjdk:8u332-jre

# set label
LABEL maintainer="Seata <seata.io>"

WORKDIR /$BASE_DIR

# ADD FORM distribution

ADD distribution/ /bin
ADD ext/apm-seata-skywalking-plugin/target/ /target
ADD ext/apm-seata-skywalking-plugin/config/ /config
ADD distribution/ /LICENSE

# set extra environment
ENV EXTRA_JVM_ARGUMENTS="-Djava.security.egd=file:/dev/./urandom -server -Xss512k -XX:+UnlockExperimentalVMOptions -XX:+UseContainerSupport XX:SurvivorRatio=10 -XX:MetaspaceSize=128m -XX:MaxMetaspaceSize=256m -XX:MaxDirectMemorySize=1024m -XX:-OmitStackTraceInFastThrow -XX:-UseAdaptiveSizePolicy -XX:+HeapDumpOnOutOfMemoryError -XX:+DisableExplicitGC -XX:+CMSParallelRemarkEnabled -XX:+UseCMSInitiatingOccupancyOnly -XX:CMSInitiatingOccupancyFraction=75 -Xloggc:/var/log/seata_gc.log -verbose:gc -Dio.netty.leakDetectionLevel=advanced"

CMD ["sh","/seata-server/bin/seata-server.sh"]
