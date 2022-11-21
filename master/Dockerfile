FROM openjdk:8-jdk-slim
		
ARG JMETER_VERSION=5.5
		
RUN apt-get clean && \
apt-get update && \
apt-get -qy install \
wget \
unzip

RUN   mkdir /jmeter \
&& cd /jmeter/ \
&& wget https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-$JMETER_VERSION.tgz \
&& tar -xzf apache-jmeter-$JMETER_VERSION.tgz \
&& rm apache-jmeter-$JMETER_VERSION.tgz

ENV JMETER_HOME /jmeter/apache-jmeter-$JMETER_VERSION/
		
ENV PATH $JMETER_HOME/bin:$PATH

EXPOSE 60000