# Use the latest Ubuntu image as the base
FROM ubuntu:latest

# Install necessary packages and tools
RUN apt-get update && apt-get install curl sudo zip unzip wget git file g++ jq maven -y  bzip2

# Download and install Cue
RUN wget https://github.com/cue-lang/cue/releases/download/v0.4.3/cue_v0.4.3_linux_amd64.tar.gz \
    && tar xf cue*.tar.gz -C /usr/bin/ \
    && chmod +x /usr/bin/cue \
    && rm cue_v0.4.3_linux_amd64.tar.gz

# Download and install PhantomJS
RUN wget -q https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2 \
    && tar -xvjf phantomjs-2.1.1-linux-x86_64.tar.bz2 \
    && mv phantomjs-2.1.1-linux-x86_64/bin/phantomjs /bin/phantomjs \
    && chmod +x /bin/phantomjs \
    && rm phantomjs-2.1.1-linux-x86_64.tar.bz2

# Update and install additional dependencies for Chrome
RUN apt-get update \
    && apt-get install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 \
    libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 \
    libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 \
    libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation \
    libappindicator1 libnss3 lsb-release xdg-utils \
    && apt-get install -y gnupg2 \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list \
    && apt-get update && apt-get -y install google-chrome-stable

# Download and install Node.js
RUN wget -q https://nodejs.org/dist/v12.22.6/node-v12.22.6-linux-x64.tar.gz \
    && tar -C /usr/local --strip-components 1 -xzf node-v12.22.6-linux-x64.tar.gz \
    && rm node-v12.22.6-linux-x64.tar.gz

# Install OpenJDK 11
RUN apt-get update \
    && apt-get install software-properties-common -y \
    && add-apt-repository ppa:openjdk-r/ppa -y \
    && apt-get update \
    && apt-get install openjdk-11-jdk  -y --no-install-recommends

# Set JAVA_HOME environment variable
ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64

# Install Python and Jira to automate PR -> JIRA
RUN apt-get update \
    && apt-get -y install python3-pip \
    && pip install jira \
    && git clone https://github.com/markchalloner/git-semver.git \
    && git-semver/install.sh \
    && apt-get update






