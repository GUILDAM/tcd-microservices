FROM java:8

# environment
EXPOSE 8080

# executable
ADD wishlist-0.0.1-SNAPSHOT.jar app.jar

# create group
RUN groupadd service
RUN chgrp service app.jar

# create user
RUN useradd -ms /bin/bash -G service booter
USER root
WORKDIR /home/booter
RUN mkdir gen/

# run app as user 'root'
RUN bash -c 'touch /app.jar'
ENTRYPOINT ["java", "-Xmx256m", "-Xss32m", "-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
