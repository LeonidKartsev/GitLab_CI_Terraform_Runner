FROM gcr.io/google.com/cloudsdktool/google-cloud-cli:alpine
RUN apk add curl net-tools bash
RUN curl -sL "https://github.com/warrensbox/terraform-switcher/releases/download/0.13.1308/terraform-switcher_0.13.1308_linux_amd64.tar.gz" | tar -xzv -C /usr/local/bin tfswitch
RUN VERSION=v0.16.1 && \
    curl -sL "https://github.com/google/go-containerregistry/releases/download/${VERSION}/go-containerregistry_Linux_x86_64.tar.gz" | tar -xzv -C /usr/local/bin crane

