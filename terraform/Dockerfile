FROM hashicorp/terraform:0.14.6

# update alpine packages
RUN apk update

# install awscli
RUN apk add python3
RUN pip3 install --upgrade pip
RUN pip3 install awscli

# install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
RUN echo "$(<kubectl.sha256) kubectl" | sha256sum --check
RUN sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# install ssh-agent
RUN apk add openssh-client
