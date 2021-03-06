FROM debian:bullseye

ENV VERSION_ANSIBLE=4.2.0 \
    VERSION_CT=0.9.0 \
    VERSION_HELM=3.6.2

RUN set -x \
 && apt-get update \
 && apt-get install --yes --no-install-recommends \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg2 \
        software-properties-common \
 && curl -f https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
 && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
 && add-apt-repository "deb [arch=amd64] http://packages.cloud.google.com/apt cloud-sdk-buster main" \
 && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian buster stable" \
 && apt-get update \
 && apt-get install --yes --no-install-recommends \
        connect-proxy \
        docker-ce \
        git \
        google-cloud-sdk \
        make \
        openssh-client \
        python3 \
        python3-pip \
        python3-setuptools \
        python3-wheel \
        rsync \
        yamllint \
 && ln -s /usr/bin/python3 /usr/bin/python \
 && ln -s /usr/bin/python3-config /usr/bin/python-config \
 && ln -s /usr/bin/python3-doc /usr/bin/python-doc \
 && curl -fsSL https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash -s -- --version "v${VERSION_HELM}" \
 && python3 -m pip install --upgrade pip \
 && python3 -m pip install ansible==${VERSION_ANSIBLE} Jinja2==3.0.1 netaddr==0.8.0 humanfriendly==9.2 openshift==0.12.1 paramiko==2.7.2 \
 && curl -Lo ct https://github.com/coreos/container-linux-config-transpiler/releases/download/v${VERSION_CT}/ct-v${VERSION_CT}-x86_64-unknown-linux-gnu \
 && chmod +x ct \
 && mv ct /usr/local/bin/ \
 && curl -fsSL https://dl.minio.io/client/mc/release/linux-amd64/mc -o /usr/local/bin/mc \
 && chmod +x /usr/local/bin/mc \
 && rm -rf /var/cache/apt/* /tmp/*

ENTRYPOINT []
