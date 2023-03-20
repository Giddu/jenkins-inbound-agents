FROM docker.io/giddu/jenkins-inbound-agent:awscli

USER root

RUN apt-get update  \
    && apt-get install -y sudo wget zip

RUN wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && rm packages-microsoft-prod.deb

RUN apt-get update \
    && apt-get install -y dotnet-sdk-3.1

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN usermod -aG sudo jenkins

USER jenkins

RUN dotnet tool install --global dotnet-sonarscanner

ENV PATH "$PATH:~/.dotnet/tools"

