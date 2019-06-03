FROM lambci/lambda:build-python3.6

MAINTAINER "sshkim" <sshkim88@gmail.com>

ENV PATH $PATH:/root/.local/bin

RUN pip3 install -U pip \
        && pip3 install -U zappa awscli

WORKDIR /tmp

RUN yum -y install wget \
        && wget -qO- https://get.haskellstack.org/ | sh \
        && wget https://hackage.haskell.org/package/pandoc-1.17.0.3/pandoc-1.17.0.3.tar.gz \
        && tar -xzf pandoc-1.17.0.3.tar.gz \
        && ( cd pandoc-1.17.0.3 && stack setup && stack install ) \
        && rm -rf pandoc* \
        && rm -rf /root/.stack/

WORKDIR /var/task

RUN python -m venv /var/venv && \
    source /var/venv/bin/activate && \
    pip install -U pip && \
    deactivate

COPY files/.bashrc /root/.bashrc

CMD ["bash"]
