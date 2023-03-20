FROM giddu/jenkins-inbound-agent:awscli

USER root

RUN apt-get update  \
    && apt-get install -y sudo wget zip

RUN wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb
RUN rm packages-microsoft-prod.deb

RUN apt-get update && \
      apt-get install -y dotnet-sdk-3.1

RUN apt-get update

RUN apt-get -y install ca-certificates curl gnupg lsb-release

RUN mkdir -m 0755 -p /etc/apt/keyrings
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg

RUN echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt-get update

RUN apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

#RUN #service docker stop
#RUN #nohup docker daemon -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock
RUN usermod -aG sudo jenkins
RUN usermod -aG docker jenkins

USER jenkins

RUN sudo service docker start

RUN dotnet tool install --global dotnet-sonarscanner

ENV PATH "$PATH:~/.dotnet/tools"

