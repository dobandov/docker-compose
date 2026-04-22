FROM jenkins/jenkins:lts

# Instalar dependencias necesarias
USER root
RUN apt-get update && apt-get install -y \
    apt-transport-https \ 
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    sudo

# Instalar Docker
# Sustituimos 'apt-key add' por una descarga directa al llavero de llaves confiables
RUN curl -fsSL https://download.docker.com/linux/debian/gpg -o /usr/share/keyrings/docker-archive-keyring.gpg
RUN curl https://get.docker.com/ > dockerinstall && chmod 777 dockerinstall && ./dockerinstall

RUN usermod -aG docker jenkins
RUN curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose

# Asegúrate de que el directorio de Jenkins sea propiedad del usuario jenkins
USER jenkins