# Wireguard - AdGuard - Unbound: All-In-One Network Security and Privacy Solution

## Overview

Welcome to the AdGuard-Unbound-WG-Easy repository! This is your go-to solution for setting up an all-in-one network security and privacy environment using Docker containers. The repository contains a Docker Compose configuration that helps you deploy a powerful, secure, and fast DNS server with AdGuard and Unbound, along with a WireGuard VPN using WG-Easy. This comprehensive setup ensures robust privacy and security for your entire network.

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Why This Solution](#why-this-solution)
4. [Prerequisites](#prerequisites)
5. [Getting Started](#getting-started)
    1. [Essential Variables](#essential-variables)
    2. [Installation](#installation)
    3. [Configuration](#configuration)
6. [Detailed Usage Guide](#detailed-usage-guide)
7. [Troubleshooting](#troubleshooting)
8. [Contribution Guidelines](#contribution-guidelines)
9. [FAQs](#faqs)
10. [License](#license)
11. [Acknowledgments](#acknowledgments)
12. [Contact Information](#contact-information)

## Features

- **AdGuard Home**: A powerful DNS server with features such as ad-blocking, web filtering, and parental controls.
- **Unbound**: A secure, validating, recursive, and caching DNS resolver with support for DNSSEC.
- **WireGuard via WG-Easy**: A fast and modern VPN that uses state-of-the-art cryptography.

## Why This Solution

DNS security and privacy are often overlooked but are critical components of online safety. This setup allows you to:

- Block ads and trackers at the network level.
- Encrypt DNS queries to prevent DNS spoofing and man-in-the-middle attacks.
- Use a VPN to encrypt all your traffic and protect your privacy.

## Prerequisites

- Docker and Docker Compose installed on a machine.
- Basic understanding of DNS, Docker, and VPN.
- A machine with a static IP address or a configured DNS resolver for hosting the services.

## Getting Started

### Essential Variables

**Before deploying the services, you must update the following essential environment variables in the `docker-compose.yml` file:**

1. **WG_HOST**: Replace this with your public IP address. Found under the `wg-easy` service environment variables.
2. **PASSWORD**: Replace this with a secure password of your choice. Also found under the `wg-easy` service environment variables.

Failure to update these variables will result in a non-functional setup. They are crucial for the proper functioning of the WireGuard VPN service.

### Installation

1. **Clone the Repository**

    ```bash
    git clone https://github.com/YourUsername/AdGuard-Unbound-WG-Easy.git
    ```

2. **Navigate to the Project Directory**

    ```bash
    cd AdGuard-Unbound-WG-Easy
    ```

3. **Deploy the Services**

    ```bash
    docker-compose up -d
    ```

### Configuration

#### AdGuard Home

Configuration files for AdGuard Home are located in `./adguard/opt-adguard-conf`.

#### Unbound

Unbound configuration files can be modified in `./unbound`.

#### WG-Easy

WG-Easy configuration files can be found under `~/.wg-easy`.

#### Using Root DNS Servers

To make full use of root DNS servers for DNS resolution, ensure to set both the **Upstream DNS servers** and **Bootstrap DNS servers** in your AdGuard Home or system settings to `127.0.0.1:5053`. This will route your DNS queries to Unbound, which is configured to leverage root DNS servers for DNS lookups.

- **Upstream DNS Servers**: Set this to `127.0.0.1:5053` to use root DNS servers.
- **Bootstrap DNS Servers**: Also set this to `127.0.0.1:5053` for the same reason.

By setting both the Upstream and Bootstrap DNS servers to `127.0.0.1:5053`, you ensure that all DNS queries are securely and accurately resolved using the root DNS servers.

## Detailed Usage Guide

- **AdGuard Home Web Panel**: Accessible at `http://<host_ip>:80`.
- **WG-Easy Web Panel**: Accessible at `http://<host_ip>:51821`.

## Troubleshooting

- **View Docker Logs**

    ```bash
    docker logs <container_name>
    ```

- **Stop and Remove Containers**

    ```bash
    docker-compose down
    ```

## Contribution Guidelines

We welcome contributions! Feel free to submit issues, feature requests, or pull requests.

## FAQs

- **Is this setup suitable for a large network?**

    Yes, this setup is scalable and can serve a network of any size.

- **How secure is this setup?**

    This setup uses state-of-the-art cryptographic algorithms, making it highly secure.
