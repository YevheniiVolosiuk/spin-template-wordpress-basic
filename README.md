# Spin WordPress Template

A customizable, developer-friendly WordPress template designed to streamline your workflow and make spinning up new WordPress projects easier than ever.

> **Note:** This project is currently under active development and is not yet ready for production use.

## Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Installation](#installation)
- [Configuration](#configuration)
    - [Changing the Domain Name](#changing-the-domain-name)
    - [Adding the WordPress Configuration File](#adding-the-wordpress-configuration-file)
    - [Installing and Trusting the SSU CA](#installing-and-trusting-the-ssu-ca)
- [Usage](#usage)
- [Notice](#notice)
- [Roadmap](#roadmap)

---

## About the Project

The **Spin WordPress Template** provides a modern, efficient boilerplate for building WordPress sites quickly. Built with speed and simplicity in mind, this template includes pre-configured settings and developer tools.

---

## Features

- **Docker**: Containerized environment setup with Docker for easy deployment, consistent development, and simplified dependency management across all platforms.
- **MariaDB**: Fast and reliable open-source database solution, optimized for scalability and compatibility with MySQL for efficient data storage and retrieval.
- **Traefik**: Integrated reverse proxy and load balancer with automated SSL management, simplifying traffic routing and enhancing security.
- **Customizable**: Easily add or remove components based on project needs, allowing for flexible configurations tailored to different project requirements.
- **Optimized for Speed**: Minimal dependencies and efficient code structure to ensure fast loading times, enhancing user experience and performance.
- **Uses serversideup/php**: An alternate approach to the official Docker images provided by PHP. These Docker images are optimized for real-world and production use cases, offering an easier developer experience.

---

## Installation

To get started, you need [Spin](https://serversideup.net/open-source/spin/docs) and [Docker](https://docs.docker.com/engine/install/) installed.

Next, run:

```
spin new YevheniiVolosiuk/spin-template-wordpress-basic --branch main
```

---

## Configuration

### Changing the Domain Name

If you want to change the domain name for your development environment:

1. Open `docker-compose.dev.yml` and navigate to line 37. Change the value for `HOST` to your desired domain name.
2. Add the same domain name to your system's `hosts` file.

### Adding the WordPress Configuration File

1. Go to the `public` directory and make a copy of the `config-simple.php` file.
2. Add the following constants to the copied `config.php` file and fill in the database values as specified in the `docker-compose.dev.yml` file under the MariaDB service.

   Ensure you use the `mariadb` service name for the `DB_HOST` value.

   ```php
   $_SERVER['HTTPS'] = 'on';
   define('FS_METHOD', 'direct');

   define('WP_HOME', 'https://change-to-your-domain-name-url-here');
   define('WP_SITEURL', 'https://change-to-your-domain-name-url-here');
   ```

### Installing and Trusting the SSU CA

To enable secure HTTPS connections in your local development environment, you need to install and trust the Server Side Up Certificate Authority (SSU CA):

1. Visit [Server Side Up CA](https://serversideup.net/ca/) and download the SSU CA certificate.
2. Follow the instructions provided to install and trust the certificate on your operating system and browser.
    - **For System Trust**: Install the certificate in your system's trusted certificate store.
    - **For Browser Trust**: Import the certificate into your browser's certificate manager.
3. Once the certificate is installed and trusted, your browser will recognize the local HTTPS connections as secure.

---

## Usage

Navigate to your project directory and run the following command:

```
spin up
```

This will start the Docker containers and set up your development environment.

---

## Notice

**This template is a work in progress.** I am actively improving its features to make it even more flexible, user-friendly, and optimized for developers. Expect regular updates, improvements, and new options that make customization easier.

Stay tuned for more features, and feel free to contribute or suggest enhancements!

---

## Roadmap

Upcoming improvements and planned features:

- **Streamlined Configuration Process**: Simplify initial setup with reduced configuration steps before and after installation.
- **Redis Integration Option**: Add an optional Redis service configuration during installation, enabling built-in support for caching to boost site performance.
- **File Naming and Organization**: Improve file names and descriptions to enhance code readability and make project navigation easier for developers.
- **Expanded Developer Documentation**: Add more detailed documentation to simplify setup, customization, and troubleshooting for all experience levels.
- **Using a Live URL for Development**: : Add support to have a live URL for the development environment, enabling seamless testing of features in a real-world-like setup.

---

Thank you for checking out **Spin WordPress Template**! I am excited to keep building and improving. If you have any feedback or want to contribute, please reach out or open a pull request.

---

Happy using! 🚀
