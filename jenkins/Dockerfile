FROM jenkins/jenkins:lts

# Cambiar a root para instalar herramientas
USER root

# Instalar dependencias mínimas y el cliente de Docker
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    sudo \
    && curl -fsSL https://get.docker.com | sh

# Añadir al usuario jenkins al grupo docker
# Nota: Esto permite que jenkins use el socket si los GIDs coinciden
RUN sudo usermod -a -G docker jenkins


# Instalar Docker Compose V2 (Sustituye a la versión 1.29.2 por ser más estable)
RUN mkdir -p /usr/local/lib/docker/cli-plugins/ && \
    curl -SL https://github.com/docker/compose/releases/download/v2.24.5/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose && \
    chmod +x /usr/local/lib/docker/cli-plugins/docker-compose && \
    ln -s /usr/local/lib/docker/cli-plugins/docker-compose /usr/local/bin/docker-compose

# Volver al usuario jenkins para seguridad
USER jenkins