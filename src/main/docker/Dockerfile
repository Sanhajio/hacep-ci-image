FROM jboss/infinispan-modules 

USER root

RUN yum install -y maven
RUN yum install -y git
RUN yum install -y vim 
RUN yum install -y wget 


USER jboss 
WORKDIR /opt/jboss

RUN mkdir ~/.m2
RUN git clone https://github.com/Sanhajio/hacep.git
RUN cp  hacep/example-maven-settings/settings.xml ~/.m2/settings.xml
RUN cd hacep && ./build-community.sh
RUN wget https://archive.apache.org/dist/activemq/5.14.2/apache-activemq-5.14.2-bin.tar.gz
RUN tar zxvf apache-activemq-5.14.2-bin.tar.gz

ENV M2_HOME=/usr/share/maven


CMD ["sh", "-c", "./apache-activemq-5.14.2/bin/activemq start && java -Xms4g -Xmx4g -Djava.net.preferIPv4Stack=true -Djgroups.bind_addr=localhost -Dgrid.buffer=5000 -Dqueue.url=tcp://localhost:61616 -Dqueue.security=true -Dqueue.usr=admin -Dqueue.pwd=admin -Dorg.apache.activemq.SERIALIZABLE_PACKAGES=\"*\" -DnodeName=node1 -jar hacep/hacep-examples/hacep-jvm-playground/target/hacep-jvm-playground-1.0-SNAPSHOT.jar"]
