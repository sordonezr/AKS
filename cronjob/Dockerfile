FROM alpine:3.18

ENV AZURE_CLI_VERSION=2.51.0

RUN apk add --no-cache \
        bash \
        curl \
        python3 \
        py3-pip \
        ca-certificates \
        openssl \
        jq \
        git \
    && apk add --no-cache --virtual .build-deps gcc libffi-dev musl-dev openssl-dev python3-dev \
    && pip install --no-cache-dir azure-cli==$AZURE_CLI_VERSION \
    && apk del .build-deps

RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
    && install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

WORKDIR /workspace

CMD ["tail", "-f", "/dev/null"]
