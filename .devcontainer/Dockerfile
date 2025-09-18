FROM ubuntu:22.04

# instale dependências básicas
RUN apt-get update && apt-get install -y curl build-essential libgmp-dev libncurses-dev zlib1g-dev

# instalar ghcup
RUN curl https://get-ghcup.haskell.org -sSf | bash -s -- -y

# definir PATH etc
ENV PATH="/root/.ghcup/bin:${PATH}"

# instalar GHC, HLS
RUN ghcup install ghc 9.6.1 && \
    ghcup install hls && \
    ghcup set ghc 9.6.1

# preparar diretório de trabalho
WORKDIR /workspace

# copiar o restante do código
COPY . /workspace

# instalar dependências do projeto
RUN cabal update && cabal build

CMD [ "bash" ]
