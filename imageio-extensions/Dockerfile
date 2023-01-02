FROM maven:3.3-jdk-8
#VOLUME ./.m2/repository /root/.m2/repository
#VOLUME ${PWD}/thumbnailer/thumbnailer
WORKDIR /thumbnailer
COPY /thumbnailer/app/target .
COPY /thumbnailer/enterypoint.sh .
VOLUME /pic
#RUN cd thumbnailer/app && mvn verify
#RUN cd thumbnailer/imageio-extensions && mvn clean install

#ENTRYPOINT cd thumbnailer/app/target && ./thumbnail.sh ../examples/jenkins1.jpg
#ENTRYPOINT bash
ENTRYPOINT bash enterypoint.sh 

