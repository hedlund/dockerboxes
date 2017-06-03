FROM ubuntu:trusty
MAINTAINER henrik@hedlund.im

# Set the locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

# Set the timezone
RUN echo "Europe/Oslo" > /etc/timezone

# Install some tools that're nice to have down the line
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y curl git nano

# Set xterm so we can use nano and other editors
ENV TERM xterm

# Let's use bash instead of sh to make it simpler to install stuff
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Configure the box to be a bit more useful
ADD bashrc /root/.bashrc
ADD bash_profile /root/.bash_profile
ADD bash_prompt /root/.bash_prompt
ADD inputrc /root/.inputrc
ENV BOXNAME Ubuntubox

# Create working directory
RUN mkdir -p /work
VOLUME [ "/work" ]
WORKDIR /work

# Run bash as the default command, but avoid using an entrypoint to we
# can easily override it...
CMD ["/bin/bash"]
