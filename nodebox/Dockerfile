FROM hedlund/ubuntubox
MAINTAINER henrik@hedlund.im

# Install Node
RUN curl -sL https://deb.nodesource.com/setup_5.x | sudo -E bash - && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install nodejs && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential

# Install some use Node tools
RUN npm install -g nodemon && \
    npm install -g express-generator && \
    npm install -g typescript tsd && \
    npm install -g yo && \
    npm install -g gulp-cli && \
    npm install -g http-server && \
    npm install -g browser-sync && \
    npm install -g babel && \
    npm install -g webpack webpack-dev-server
