FROM hedlund/ubuntubox
MAINTAINER henrik@hedlund.im

# Install Java 6, 7 & 8, and Maven
RUN DEBIAN_FRONTEND=noninteractive apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common && \
    DEBIAN_FRONTEND=noninteractive add-apt-repository ppa:webupd8team/java -y && \
    DEBIAN_FRONTEND=noninteractive apt-get update -y && \
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y oracle-java6-installer && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y oracle-java7-installer && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y oracle-java8-installer && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install maven && \
    DEBIAN_FRONTEND=noninteractive apt-get remove software-properties-common -y && \
    DEBIAN_FRONTEND=noninteractive apt-get autoremove -y && \
    DEBIAN_FRONTEND=noninteractive apt-get clean

# Install jEnv
RUN git clone https://github.com/gcuisinier/jenv.git /root/.jenv
ENV PATH ${PATH}:/root/.jenv/bin
RUN eval "$(jenv init -)"  && \
    for version in $(ls /usr/lib/jvm/); do jenv add "/usr/lib/jvm/$version/"; done && \
    jenv rehash && \
    jenv enable-plugin maven && \
    jenv enable-plugin gradle && \
    jenv enable-plugin ant && \
    echo "eval \"\$(jenv init -)\"" >> /root/.bashrc

# Export the dependencies directories as volumes
RUN mkdir -p /root/.m2 && \
    mkdir -p /root/.gradle
VOLUME [ "/root/.m2", "/root/.gradle" ]
