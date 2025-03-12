# Using 'ubuntu' as the base image here
FROM ubuntu:20.04

# setting the working directory
WORKDIR /opt/aem

# Avoid asking to configure the tzdata
# YOU NEED TO CHANGE THE TZ VARIABLE IN THE REGION YOU WANT TO WORK
ENV TZ=Australia/Sydney
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Copy the license file
COPY license.properties .

# Copy Quickstart jar file
# YOU NEED TO CHANGE THE VERSION BASED ON WHICH ONE YOU NEED
COPY cq-quickstart-6.5.0.jar cq-quickstart.jar

# Install Java and other tools
RUN apt-get update && \
    apt-get install -y ca-certificates apt-transport-https && \
    apt-get install -y curl && \
    apt-get install -y sudo && \
    apt-get install -y vim && \
    apt-get install -y wget && \
    apt-get install -y zip && \
    apt-get install -y software-properties-common && \
    apt-get install -y openjdk-11-jdk

# Unack the Jar file
RUN java -jar cq-quickstart.jar -unpack

# Clean Up apt Cache to Reduce Image Size
RUN rm -rf /var/lib/apt/lists/*