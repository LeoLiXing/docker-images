FROM leostar/centos-ssh:latest

ADD  jdk-8u221-linux-x64.tar.gz  /usr/local/

ENV JAVA_HOME /usr/local/jdk1.8.0_221
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH $PATH:$JAVA_HOME/bin

