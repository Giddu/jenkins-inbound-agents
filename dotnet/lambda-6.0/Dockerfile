FROM giddu/jenkins-inbound-agent:awscli

USER root

RUN apt-get update  \
    && apt-get install -y wget  \
    && apt-get install -y zip

RUN wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb

RUN apt-get update && \
      apt-get install -y dotnet-sdk-6.0

USER jenkins

RUN dotnet tool install --global dotnet-sonarscanner
RUN dotnet tool install -g Amazon.Lambda.Tools

ENV PATH "$PATH:~/.dotnet/tools"