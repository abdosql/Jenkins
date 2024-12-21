FROM jenkins/jenkins:lts

USER root

# Install required packages
RUN apt-get update && \
    apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    php \
    php-cli \
    php-xml \
    php-zip \
    php-json \
    php-curl \
    php-mbstring \
    php-intl \
    php-pdo \
    php-mysql \
    php-tokenizer \
    php-xmlwriter \
    sudo \
    unzip

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    chmod +x /usr/local/bin/composer

# Install Symfony CLI
RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | bash && \
    apt install -y symfony-cli

# Install Docker
RUN curl -fsSL https://get.docker.com | sh

# Install Docker Compose
RUN curl -L "https://github.com/docker/compose/releases/download/v2.20.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

# Add jenkins user to sudo group and allow passwordless sudo
RUN usermod -aG sudo jenkins && \
    echo "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

USER jenkins
