ARG VARIANT=1.18-bullseye
FROM golang:$VARIANT as dev

ENV USERNAME vscode
ENV HOME /home/$USERNAME

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
  && apt-get -y install --no-install-recommends apt-utils sudo

# ユーザー追加とsudo権限追加
RUN groupadd $USERNAME && useradd -s /bin/bash --gid $USERNAME -m $USERNAME \
  && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
  && chmod 0440 /etc/sudoers.d/$USERNAME \
  && EXISTING_NON_ROOT_USER="${USERNAME}"

USER $USERNAME
WORKDIR $HOME/workspace
