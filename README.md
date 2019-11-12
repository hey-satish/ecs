# ecs-terraform
ecs with terraform


IN the above repository we are building the image and pushing it using docker , that code is taken by the Dockerfile which running 

create a DOckerfile and add the below series of commands which install teh tomcat server and java '

FROM amazonlinux
RUN yum update -y
RUN yum install -y java-1.8.0-openjdk-devel wget curl
RUN yum install -y tar.x86_64
RUN mkdir /usr/local/tomcat
WORKDIR /usr/local/tomcat/
RUN wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.5.46/bin/apache-tomcat-8.5.46.tar.gz
RUN tar xvfz apache-tomcat-8.5.46.tar.gz
RUN mv apache-tomcat-8.5.46/* /usr/local/tomcat/
WORKDIR /usr/local/tomcat/webapps
RUN curl -O -L https://github.com/AKSarav/SampleWebApp/raw/master/dist/SampleWebApp.war
EXPOSE 8080

CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]


