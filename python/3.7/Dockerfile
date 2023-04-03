FROM giddu/jenkins-inbound-agent:sonarscanner

ENV PYTHON_VERSION=3.7

USER root

RUN apt-get update

RUN apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
    libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
    xz-utils tk-dev libffi-dev liblzma-dev

USER jenkins

RUN curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash

ENV PYENV_ROOT "$HOME/.pyenv"
ENV PATH "$PYENV_ROOT/bin:$PATH"

#if command -v pyenv 1>/dev/null 2>&1; then
RUN eval "$(pyenv init --path)"
#fi
RUN eval "$(pyenv virtualenv-init -)"

RUN pyenv -v

