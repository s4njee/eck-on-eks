FROM launcher.gcr.io/google/debian9
RUN apt-get update
RUN apt-get install -y bash curl wget gnupg apt-transport-https apt-utils lsb-release
RUN wget -O - https://debian.neo4j.org/neotechnology.gpg.key | apt-key add -
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN echo 'deb https://debian.neo4j.org/repo stable/' | tee -a /etc/apt/sources.list.d/neo4j.list
RUN echo "neo4j-enterprise neo4j/question select I ACCEPT" | debconf-set-selections
RUN echo "neo4j-enterprise neo4j/license note" | debconf-set-selections

RUN apt-get update && apt-get install -y neo4j-enterprise=1:3.5.14

RUN mkdir /data
RUN apt update
RUN apt install -y python3 python3-pip
RUN pip3 install awscli
ADD restore.sh /scripts/restore.sh
RUN chmod +x /scripts/restore.sh
WORKDIR /scripts
CMD ["/scripts/restore.sh"]
