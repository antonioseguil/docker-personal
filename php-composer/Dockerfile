# Usa la imagen base de Ubuntu
FROM ubuntu:22.04

# Establece la zona horaria (ajusta a tu zona horaria)
ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=America/Lima

# Instala las dependencias necesarias
RUN apt-get update && apt-get install -y \
    software-properties-common \
    git \
    zsh \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    libzip-dev \
    && apt-get clean

# Configura la zona horaria
RUN apt-get install -y tzdata

# Agrega el repositorio de Ondřej Surý para PHP
RUN add-apt-repository ppa:ondrej/php -y && \
    apt-get update && \
    apt-get install -y \
    php8.2 \
    php8.2-cli \
    php8.2-fpm \
    php8.2-mbstring \
    php8.2-xml \
    php8.2-mysql \
    php8.2-curl \
    php8.2-zip \
    php8.2-gd && \
    apt-get clean

# Instala Node.js (versión LTS)
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs && \
    apt-get clean

# Obtiene la última versión de Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Instala Oh My Zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Cambia el shell por defecto a zsh
RUN chsh -s $(which zsh)

# Establece el directorio de trabajo
WORKDIR /home/antonio/proyectos-trabajo/c3app/

# Comando por defecto
CMD ["zsh"]
