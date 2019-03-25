FROM ubuntu:latest

# Configure locale, or the Python 3 won't work properly
ENV LANG=C.UTF-8
ENV SPARK_VERSION=2.4.0
ENV HADOOP_VERSION=2.7
ENV JAVA_HOME=/usr/lib/jvm/java-8-oracle
ENV SPARK_HOME=/opt/spark-${SPARK_VERSION}
ENV SPARK_ARCHIVE=http://apache.mirrors.spacedump.net/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
ENV PATH=$PATH:${SPARK_HOME}/bin

# Setup prerequisites
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install software-properties-common

# Setup Python
RUN apt-get install -y python3-pip python3-setuptools python3.7-venv python3.7
RUN pip3 install --upgrade pip
# Configures `python` command to use Python 3.7
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.7 1

# Setup Java
RUN apt-add-repository ppa:webupd8team/java -y
RUN echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
RUN apt-get install -y oracle-java8-installer

# Download and install Spark. Spark must be installed on all nodes
RUN wget ${SPARK_ARCHIVE} -P /tmp/
RUN tar -xzf /tmp/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz -C /tmp/
RUN mv /tmp/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} ${SPARK_HOME}
RUN rm /tmp/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz

WORKDIR ${SPARK_HOME}
