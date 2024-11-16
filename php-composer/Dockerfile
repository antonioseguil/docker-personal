# Usa la imagen base de PHP con FPM
FROM php:8.2-fpm

# Instala las dependencias del sistema
RUN apt-get update && apt-get install -y \
    git \
    curl \
    zsh \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip \
    libzip-dev

# Instala Node.js (versión LTS)
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs

# Limpia la caché
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Instala extensiones de PHP
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip

# Obtiene la última versión de Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Instala Oh My Zsh
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Cambia el shell por defecto a zsh
RUN chsh -s $(which zsh)

# Establece el directorio de trabajo
WORKDIR /home/antonio/proyectos-trabajo/c3app/