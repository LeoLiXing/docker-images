FROM ostar/centos-ssh:latest

ADD  jdk-8u221-linux-x64.tar.gz  /usr/local/
ADD  apache-tomcat-8.5.39.tar.gz  /usr/local/

ENV JAVA_HOME /usr/local/jdk1.8.0_221
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV CATALINA_HOME /usr/local/apache-tomcat-8.5.39
ENV CATALINA_BASE /usr/local/apache-tomcat-8.5.39
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/lib:$CATALINA_HOME/bin

#ADD ./hello-world.war /usr/local/apache-tomcat-8.5.39/webapps

EXPOSE 8080

CMD ["/bin/sh","-c","/usr/sbin/sshd -D & /usr/local/apache-tomcat-8.5.39/bin/catalina.sh run"]
