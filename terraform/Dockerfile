FROM hashicorp/terraform:0.14.6

RUN apk --no-cache add python3 py3-pip curl openssh-client

# install awscli
RUN pip3 install --upgrade pip
RUN pip3 install awscli

# install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
RUN echo "$(<kubectl.sha256) kubectl" | sha256sum --check
RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# configure ssh
RUN mkdir -p ~/.ssh
RUN chmod 700 ~/.ssh
RUN ssh-keyscan github.com >> ~/.ssh/known_hosts
