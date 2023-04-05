FROM giddu/jenkins-inbound-agent:sonarscanner

ENV PYTHON_VERSION=3.7.16

USER root

RUN apt-get update && apt-get install -y wget build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libsqlite3-dev libreadline-dev libffi-dev curl libbz2-dev -y


RUN wget https://www.python.org/ftp/python/$PYTHON_VERSION/Python-$PYTHON_VERSION.tar.xz
RUN tar -xf Python-$PYTHON_VERSION.tar.xz
RUN mv Python-$PYTHON_VERSION /opt/
RUN cd /opt/Python-$PYTHON_VERSION && ./configure --enable-optimizations --enable-shared && make && make altinstall
RUN ldconfig /opt/Python$PYTHON_VERSION

USER jenkins

RUN python3.7 -m ensurepip --upgrade
RUN python3.7 -m pip install zappa

ENV PATH "$PATH:~/.local/bin"
RUN ~/.local/bin/zappa --version