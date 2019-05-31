FROM mligus/zappa:python3.6

RUN yum -y install wget

WORKDIR /tmp

RUN wget -qO- https://get.haskellstack.org/ | sh
RUN wget https://hackage.haskell.org/package/pandoc-1.17.0.3/pandoc-1.17.0.3.tar.gz \ 
	&& tar xvzf pandoc-1.17.0.3.tar.gz \
	&& rm pandoc-1.17.0.3.tar.gz

WORKDIR pandoc-1.17.0.3

RUN stack setup \
	&& stack install

ENV PATH="/root/.local/bin:${PATH}"

WORKDIR /var/task

RUN pip install -U pip setuptools wheel

CMD ['zappa']

