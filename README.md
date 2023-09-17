# Wireguard - AdGuard - Unbound: All-In-One Network Security and Privacy Solution

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Why Choose This Solution](#why-choose-this-solution)
4. [Prerequisites](#prerequisites)
5. [Getting Started](#getting-started)
   - [Installation](#installation)
   - [Configuration](#configuration)
6. [Detailed Usage Guide](#detailed-usage-guide)

## Overview

Welcome to the AdGuard-Unbound-WG-Easy project, a comprehensive Docker Compose setup designed for robust network security and privacy. This repository includes configurations for AdGuard Home, Unbound, and WireGuard via WG-Easy.

## Features

- **AdGuard Home**: Blocks ads and trackers and provides web filtering and parental controls.
- **Unbound**: Validates, caches, and recursively resolves DNS queries, supporting DNSSEC.
- **WireGuard via WG-Easy**: Offers a modern, fast VPN with top-notch cryptography.

## Why Choose This Solution

This setup provides:

- Network-level ad and tracker blocking.
- DNS query encryption for added security.
- VPN for secure and private internet access.

## Prerequisites

- Installed Docker and Docker Compose.
- Basic knowledge of DNS, Docker, and VPN concepts.
- A host machine with a static IP or a configured DNS resolver.

## Getting Started

### Installation

1. **Clone the Repository**

    ```bash
    git clone https://github.com/wireguard-adguard-unbound
    ```

2. **Navigate to the Project Directory**

    ```bash
    cd wireguard-adguard-unbound
    ```

3. **Update Essential Variables**

    Update these essential variables in the `docker-compose.yml`:

    - `WG_HOST`: Your public IP address.
    - `PASSWORD`: A secure password for WireGuard.
    
4. **Deploy the Services**

    ```bash
    docker-compose up -d
    ```

### Configuration

- Access the AdGuard Home web panel at `http://<host_ip>:80`.
- Access the WG-Easy web panel at `http://<host_ip>:51821`.

#### Using Root DNS Servers

To make full use of root DNS servers for DNS resolution, ensure to set both the **Upstream DNS servers** and **Bootstrap DNS servers** in your AdGuard Home or system settings to `127.0.0.1:5053`. This will route your DNS queries to Unbound, which is configured to leverage root DNS servers for DNS lookups.
- **Upstream DNS Servers**: Set this to `127.0.0.1:5053` to use root DNS servers.
- **Bootstrap DNS Servers**: Also set this to `127.0.0.1:5053` for the same reason.
By setting both the Upstream and Bootstrap DNS servers to `127.0.0.1:5053`, you ensure that all DNS queries are securely and accurately resolved using the root DNS servers.

## Detailed Usage Guide

AdGuard Home configuration files in `./adguard/opt-adguard-conf`.
Unbound configurations in `./unbound`.
WG-Easy configurations in `~/.wg-easy`.


