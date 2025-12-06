# Use an official Ubuntu image as the base
FROM ubuntu:22.04

# Set environment variable to avoid tzdata configuration prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install essential dependencies
RUN apt-get update && apt-get install -y \
  apt-transport-https \
  ca-certificates \
  curl \
  software-properties-common \
  lsb-release \
  gnupg2 \
  git \
  bash \
  sudo \
  unzip \
  && rm -rf /var/lib/apt/lists/*

# Install Docker
RUN curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
RUN usermod -aG docker vscode

# Install Docker Compose
RUN curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose

# Install additional utilities (optional)
RUN apt-get update && apt-get install -y vim

# Expose Docker API port (if needed for external connections)
EXPOSE 2375

# Set the default shell
CMD ["bash"]
