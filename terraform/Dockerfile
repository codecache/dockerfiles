FROM hashicorp/terraform:0.14.6

RUN apk -q --no-cache add curl openssh-client bash python3 py3-pip

# install awscli
RUN pip3 install -q --upgrade pip
RUN pip3 install -q awscli

# install kubectl
RUN curl -sLO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# configure ssh
RUN mkdir -p ~/.ssh
RUN chmod 700 ~/.ssh
RUN ssh-keyscan github.com >> ~/.ssh/known_hosts
RUN touch ~/.ssh/id_rsa
RUN chmod 600 ~/.ssh/id_rsa

# configure bash as the default shell
RUN ln -sf bash /bin/ash
