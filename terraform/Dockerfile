FROM hashicorp/terraform:0.14.6

RUN apk -q --no-cache add openssh-client python3 py3-pip

# install awscli
RUN pip3 install -q --upgrade pip
RUN pip3 install -q awscli

# configure ssh
RUN mkdir -p ~/.ssh
RUN mkdir -p /github/home/.ssh
RUN chmod 700 ~/.ssh
RUN chmod 700 /github/home/.ssh
RUN ssh-keyscan github.com >> ~/.ssh/known_hosts
RUN ssh-keyscan github.com >> /github/home/.ssh/known_hosts
RUN touch ~/.ssh/id_rsa
RUN touch /github/home/.ssh/id_rsa
RUN chmod 600 ~/.ssh/id_rsa
RUN chmod 600 /github/home/.ssh/id_rsa
