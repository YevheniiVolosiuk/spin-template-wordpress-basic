# Spin WordPress Template

A customizable, developer-friendly WordPress template designed to streamline your workflow and make spinning up new WordPress projects easier than ever.

## Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Folder Structure](#folder-structure)
- [Contributing](#contributing)
- [License](#license)

---

## About the Project

The **Spin WordPress Template** provides a modern, efficient boilerplate for building WordPress sites quickly. Built with speed and simplicity in mind, this template includes pre-configured settings, developer tools.

---

## Features

- **Docker**: 
- **MariaDB**: 
- **Tarefick**: 
- **Customizable**: Easily add or remove components based on project needs.
- **Optimized for Speed**: Minimal dependencies to ensure fast loading times.

---

## Installation

To get started, you need [Spin](https://serversideup.net/open-source/spin/docs) and [Docker](https://docs.docker.com/engine/install/) installed.

### 1. Install Template

```
spin new YevheniiVolosiuk/spin-template-laravel-basic --branch main
```
### 2. Make Modification
```
If you whant change domain name for dev env. you need:
1. Go to  docker-compose.dev.yml to line 37 and change value for HOST. 
2. next add same domain name to your host file in a PC.
```
### 3.Add wp config file
```
Go to public dir and make copy for a default config-simple.php file.
Next add few new constans to a file and fill DB values as in docker-compose.dev.yml in a mariaDB service.
Don't forget to use mariadb service name for DB_HOST value.

Copy and add this directives to your config.php
$_SERVER['HTTPS'] = 'on';
define('FS_METHOD', 'direct');

define( 'WP_HOME', 'https://change-to-your-domain-name-url-hire' );
define( 'WP_SITEURL', 'https://change-to-your-domain-name-url-hire' );
```
### 3.Spin Project
Next cd to your project and run command:
```
spin up
```

---

## Notice

**This template is a work in progress.** I am actively improving its features to make it even more flexible, user-friendly, and optimized for developers. Expect regular updates, improvements, and new options that make customization easier.

Stay tuned for more features, and feel free to contribute or suggest enhancements!

---

## Roadmap

Upcoming improvements and planned features:

Upcoming improvements and planned features:

- **Streamlined Configuration Process**: Simplify initial setup with reduced configuration steps before and after installation.
- **Redis Integration Option**: Add an optional Redis service configuration during installation, enabling built-in support for caching to boost site performance.
- **File Naming and Organization**: Improve file names and descriptions to enhance code readability and make project navigation easier for developers.
- **Expanded Developer Documentation**: Add more detailed documentation to simplify setup, customization, and troubleshooting for all experience levels.

---

Thank you for checking out **Spin WordPress Template**! We’re excited to keep building and improving. If you have any feedback or want to contribute, please reach out or open a pull request. Together, let’s make this a go-to template for WordPress development.

---

Happy coding! 🚀
