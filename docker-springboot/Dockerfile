FROM leostar/jdk:8

ADD ./springboot-helloworld-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8092

ENTRYPOINT ["/bin/sh","-c","/usr/sbin/sshd -D & java -jar /app.jar"]
