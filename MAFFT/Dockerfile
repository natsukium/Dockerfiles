FROM alpine:latest
LABEL maintainer "natsukium <tomoya.matsumoto@natsukium.com>"
LABEL org.opencontainers.image.url https://github.com/natsukium/Dockerfiles/tree/master/MAFFT
LABEL org.opencontainers.image.source https://github.com/natsukium/Dockerfiles/blob/master/MAFFT/Dockerfile
LABEL org.opencontainers.image.documentation https://github.com/natsukium/Dockerfiles/blob/master/MAFFT/README.md
LABEL org.opencontainers.image.description "MAFFT (https://mafft.cbrc.jp/alignment/software/) is a multiple sequence alignment program for unix-like operating systems.  It offers a range of multiple alignment methods, L-INS-i (accurate; for alignment of <∼200 sequences), FFT-NS-2 (fast; for alignment of <∼30,000 sequences), etc."

WORKDIR build

ARG MAFFT_VERSION=7.475
ENV SOURCE mafft-${MAFFT_VERSION}-without-extensions

RUN apk update && \
  apk add --no-cache --virtual build-deps curl \
    gcc \
    make \
    musl-dev && \
  apk add --no-cache bash && \
  curl -O https://mafft.cbrc.jp/alignment/software/${SOURCE}-src.tgz && \
  gunzip -cd ${SOURCE}-src.tgz | tar xvf - && \
  cd ${SOURCE}/core && \
  make clean && \
  make && \
  make install && \
  apk del --purge build-deps && \
  rm -rf *

WORKDIR /workdir

ENTRYPOINT ["mafft"]
CMD ["--help"]
