FROM buildpack-deps:xenial

# CircleCI requirements
RUN perl -MCPAN -e 'install TAP::Parser' \
	&& perl -MCPAN -e 'install XML::Generator'

RUN git clone https://github.com/sstephenson/bats.git \
	&& cd bats \
	&& ./install.sh /usr/local \
	&& cd .. \
	&& rm -rf bats

RUN apt-get update \
	&& apt-get -y install lsb-release unzip

# Java 8
RUN apt-get update \
	&& apt-get -y install software-properties-common python-software-properties \
	&& apt-get update \
	&& apt-get -y install openjdk-8-jdk

# awscli
RUN apt-get -y install python3-pip \
	    && pip3 install --upgrade awscli

# leiningen
RUN wget https://raw.githubusercontent.com/technomancy/leiningen/2.5.3/bin/lein -O /bin/lein \
	&& chmod +x /bin/lein
