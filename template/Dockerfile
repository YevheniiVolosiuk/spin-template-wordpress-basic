############################################
# Base Image
############################################
FROM serversideup/php:8.3-fpm-apache AS base


# Check if the 'public' folder exists; if not, create it and then download and extract WordPress
#RUN mkdir -p public && \
#    wget -c https://wordpress.org/latest.tar.gz -O - | tar -xz -C public/ --strip=1 wordpress/


############################################
# Development Image
############################################
FROM base AS development
# Switch to root so we can do root things
USER root

# Save the build arguments as a variable
ARG USER_ID
ARG GROUP_ID

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
    chmod +x wp-cli.phar && \
    mv wp-cli.phar /usr/local/bin/wp

# Use the build arguments to change the UID 
# and GID of www-data while also changing 
# the file permissions for NGINX
RUN docker-php-serversideup-set-id www-data $USER_ID:$GROUP_ID && \
    \
    # Update the file permissions for our NGINX service to match the new UID/GID
    docker-php-serversideup-set-file-permissions --owner $USER_ID:$GROUP_ID --service apache

# Drop back to our unprivileged user
USER www-data

############################################
# Production Image
############################################

# Since we're calling "base", production isn't
# calling any of that permission stuff
FROM base AS production

# Copy our app files as www-data (33:33)
COPY --chown=www-data:www-data . /var/www/html
