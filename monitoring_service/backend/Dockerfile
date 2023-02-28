# Prepare stage for multistage image build
## START OF STAGE0 ##
FROM python:3.6-slim-stretch

# # CREATE APP USER ##
# Set umask
RUN sed -i "s|umask 022|umask 027|g" /etc/profile

# Create the home directory for the new app user.
RUN mkdir -p /usr/app
RUN mkdir -p /usr/app/bin
RUN mkdir -p /usr/app/monitoring
RUN mkdir -p /usr/app/test/resources
RUN mkdir -p /usr/app/images

# Set the home directory to our app user's home.
ENV APP_HOME=/usr/app
ENV UID=166
ENV GID=166
ENV USER_NAME=eguser
ENV GROUP_NAME=eggroup
ENV ENV="/etc/profile"

# Create an app user so our program doesn't run as root.
RUN apt-get -y update &&\
    groupadd -r -g $GID $GROUP_NAME &&\
    useradd -r -u $UID -g $GID -d $APP_HOME -s /sbin/nologin -c "Docker image user" $USER_NAME

RUN apt-get install -y --fix-missing \
    build-essential \
    cmake \
    gfortran \
    git \
    wget \
    curl \
    graphicsmagick \
    libgraphicsmagick1-dev \
    libatlas-dev \
    libavcodec-dev \
    libavformat-dev \
    libgtk2.0-dev \
    libjpeg-dev \
    liblapack-dev \
    libswscale-dev \
    pkg-config \
    python3-dev \
    python3-numpy \
    software-properties-common \
    zip \
    && apt-get clean && rm -rf /tmp/* /var/tmp/*

# Set the working directory.
WORKDIR $APP_HOME

# Copy the application & scripts
COPY config.py requirements.txt run.py constants.py clientsdk.py restclient.py $APP_HOME/
COPY monitoring $APP_HOME/monitoring/
COPY configs/*.sh $APP_HOME/bin

RUN chmod 750 $APP_HOME &&\
    chmod -R 550 $APP_HOME/bin &&\
    mkdir -p -m 750 $APP_HOME/log &&\
    mkdir -p -m 700 $APP_HOME/ssl &&\
    chown -R $USER_NAME:$GROUP_NAME $APP_HOME

# Exposed port
EXPOSE 9997

# Change to the app user.
USER $USER_NAME
# FROM registry.cn-hangzhou.aliyuncs.com/sonobuoy-cwx/build-image:demo

# Install requirements
#RUN pip install --upgrade pip setuptools wheel
#RUN pip install -r requirements.txt --verbose

# Execute script & application
#ENTRYPOINT ["sh", "./bin/start.sh"]
