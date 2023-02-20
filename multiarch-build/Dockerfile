FROM arm64v8/debian:10-slim

RUN apt-get update \
  && apt-get install -y curl \
  && rm -rf /var/lib/apt/lists/*

ENTRYPOINT [ "curl" ]
