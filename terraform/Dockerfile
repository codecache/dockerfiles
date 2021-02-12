FROM hashicorp/terraform:0.14.6

RUN apk --no-cache add curl openssh-client 

# install awscli
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install

# install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# configure ssh
RUN mkdir -p ~/.ssh
RUN chmod 700 ~/.ssh
RUN ssh-keyscan github.com >> ~/.ssh/known_hosts
