FROM ruby:3.1.4

ARG UNAME=devenv
ARG UID=1001
ARG GID=1001

RUN DEBIAN_FRONTEND=noninteractive \
    apt-get -y update && \
    apt-get -y upgrade && \
    apt-get -y install --no-install-recommends \
      sqlite3 libsqlite3-dev \
      nodejs \
      git \
      wget \
      vim

RUN groupadd -g $GID -o $UNAME && \
    useradd -m -d /$UNAME -u $UID -g $GID -o -s /bin/bash $UNAME

COPY --chown=$UID:$GID . /$UNAME

USER $UNAME

WORKDIR /$UNAME

RUN bundle install

CMD ["sleep", "infinity"]

