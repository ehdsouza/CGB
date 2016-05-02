# set the base image to Ubuntu
FROM ubuntu:latest

# Author
MAINTAINER Erika Dsouza erika27desouza@gmail.com

# Install dependencies and bowtie, bowtie2, and samtools
RUN apt-get update && apt-get install -y \
	wget \
	unzip \
	python3 \
	python-pip \
	bowtie \
	bowtie2 \
	samtools \
	&& apt-get clean
RUN pip install beautifulsoup4

# Install breseq from http
WORKDIR /usr/local/
RUN wget http://github.com/barricklab/breseq/releases/download/v0.26.0/breseq-0.26.0-Linux-x86_64.tar.gz
RUN tar -zxvf breseq-0.26.0-Linux-x86_64.tar.gz

# add breseq to path
ENV PATH /usr/local/breseq-0.26.0-Linux-x86_64/bin:$PATH

# copy HTML
ADD static/ /src
WORKDIR /src

# Run http server on port 8080
EXPOSE  8080
CMD ["python3", "-m", "http.server", "8080"]

# Cleanup
RUN rm -rf breseq-0.26.0-Linux-x86_64.tar.gz
RUN apt-get clean




