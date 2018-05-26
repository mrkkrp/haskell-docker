FROM debian:stretch

ENV LANG C.UTF-8

RUN echo 'deb http://ppa.launchpad.net/hvr/ghc/ubuntu trusty main' > /etc/apt/sources.list.d/ghc.list
RUN apt-get update -qq
RUN apt-get install -qy gnupg
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F6F88286
RUN apt-get install -qy --allow-unauthenticated cabal-install-2.2 ghc-8.4.2 happy alex zlib1g-dev libtinfo-dev libsqlite3-0 libsqlite3-dev ca-certificates g++ git curl git make automake autoconf gcc perl python3 texinfo xz-utils lbzip2 patch openssh-client sudo
RUN curl -fSL https://github.com/commercialhaskell/stack/releases/download/v1.6.5/stack-1.6.5-linux-x86_64-static.tar.gz -o stack.tar.gz
ENV PATH /root/.cabal/bin:/root/.local/bin:/opt/cabal/2.2/bin:/opt/ghc/8.4.2/bin:$PATH

# Create a normal user.
RUN adduser circleci --disabled-password
RUN echo "circleci ALL = NOPASSWD : ALL" > /etc/sudoers.d/ghc
USER circleci

WORKDIR /home/ghc/

CMD ["bash"]
