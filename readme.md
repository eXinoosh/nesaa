# Nesa Bootstrap

![Nesa Bootstrap Process](https://raw.githubusercontent.com/nesaorg/bootstrap/master/images/bootstrap.gif)

Welcome to the official repository for the Nesa Bootstrap script! This repository contains the necessary tools and scripts to set up and configure your Nesa node efficiently.

## Overview

This repository contains wizardry aimed at making the deployment and configuration of a Nesa node easier. It handles everything from checking system prerequisites to configuring Docker containers, setting up node types, connecting to the Nesa network, and ultimately providing a streamlined way to get your Nesa node up and running with minimal manual intervention.

## Features

- **Cross-Platform Support**: Supports Linux, macOS, and Windows (via WSL).
- **Automated Setup**: Automatically installs required dependencies like Docker, Gum, and jq.
- **Node Configuration**: Allows configuration of nodes as Validators or Miners, with support for both distributed and non-distributed miners.
- **Swarm Support**: Supports joining existing swarms or creating new ones for distributed mining tasks.
- **Model Selection**: Easily select or specify a model to run on your miner node.
- **Auto-Updates**: Nodes automatically receive updates to keep your system up to date with the latest improvements and features.

## Prerequisites

Before running the bootstrap script, ensure your system meets the following requirements:

### Hardware Requirements

- **CPU**: Multi-core processor
- **Memory**: Minimum 4 GB RAM
- **Storage**: 50 GB free disk space (more is recommended during testnet to allow us to send other jobs in order to test your node's capabilities)
- **Network**: Stable internet connection
- **GPU**: CUDA-enabled GPUs recommended. MPS is also supported. CPU mining is available, but not for all models.

**note**: For the testnet miner campain, we highly encourage closer to 16GB of RAM and 100GB of disk space. This is due to the nature of the testnet and the need to test the capabilities of the network.

### Software Requirements

- **Operating System**: Ubuntu, Debian, CentOS, macOS, Windows (with WSL). Other Linux distributions may work but are not officially supported.
- **Docker**: Required for running Nesa nodes ([installation guide](https://docs.docker.com/get-docker/))
- **Nvidia Container Toolkit**: For systems with an NVIDIA GPU ([example installation script](https://raw.githubusercontent.com/nesaorg/bootstrap/master/helpers/install_nvidia_container_toolkit.sh))
- **Curl**: To download and run the bootstrap script ([installation guide](https://curl.se/docs/install.html))

### Configuration Preparation

Before starting the bootstrap script, you’ll need to have the following information ready:

- **Private Key**: Required for registering your miner and receiving rewards. Refer to the [FAQ](./FAQ.md#2-why-do-i-need-to-provide-a-private-key-when-setting-up-a-miner-node) on how to obtain your private key.
- **Hugging Face API Key**: Necessary for accessing models hosted on Hugging Face. Refer to the [FAQ](./FAQ.md#7-how-do-i-obtain-a-hugging-face-api-key) on how to obtain an API key.
- **Referral Code** (optional): If you were referred by another user, have their wallet address or public key hex ready.

Having these ready will ensure a smooth and efficient configuration process.

## Quickstart

To get started quickly, use the following command to download and execute the bootstrap script:

```bash
bash <(curl -s https://raw.githubusercontent.com/nesaorg/bootstrap/master/bootstrap.sh)
```

### Configuration Steps

1. **Choose a Moniker**: Provide a unique name for your node.
2. **Select Node Type**: Decide whether your node will act as a Validator or Miner. See below for details on each type.
3. **Provide Wallet Private Key**: Enter your wallet private key for  miner registration and to receive rewards.
4. **Enter Referral Code** (optional): If applicable, provide the referral code.
6. **Finalize Configuration**: Review and confirm the configuration before starting your node. The bootstrap script will provide a summary of your configuration and allow you to make changes before proceeding.

## Node Types

### Validator

Validators are responsible for securing the network by participating in consensus, committing new blocks to the blockchain, and voting on proposals. Validators require a significant amount of staked tokens and are selectively chosen. Currently, validators are not open for public deployment, and participants are encouraged to run miner nodes instead.

### Miner

Miners on the Nesa network perform computationally heavy tasks like running AI model inference. Miners contribute to the network's operation and earn rewards for their participation. The specific configuration of miners (distributed or non-distributed) is handled internally by the network.

## Node Identification and Security

Each node is assigned a unique node ID upon creation. This ID, along with a nonce and timestamp, is used to sign messages sent from the node to the network. This signing process ensures the authenticity of each node's communications without requiring the storage of private keys on our servers. The private key remains securely on the miner's machine and is used only for local signing operations.

## Advanced Setup

For users who need more control over the setup process, the script offers an "Advanced Wizardry" mode that allows you to fine-tune your node's configuration manually via the config files in `~/.nesa/env`. It is recommended to run the script once in Wizardry mode to generate the base config. Then you can modify the config files to your liking if needed. Running the script again in "Advanced Wizardry" mode will load the existing config from previous runs or manual edits, allowing you to skip the initial setup steps.

## Troubleshooting

If you encounter any issues during setup or operation, here are some general troubleshooting steps:

- **Docker Issues**: Ensure Docker is properly installed and running.
- **Permission Errors**: Add your user to the Docker group to avoid permission issues:
  ```bash
  sudo usermod -aG docker $USER
  newgrp docker
  ```
- **NVIDIA Errors**: Double-check that your NVIDIA driver, CUDA, and the NVIDIA Container Toolkit are installed correctly.

For more detailed troubleshooting steps, please refer to our [Troubleshooting Guide](./Troubleshooting.md).

## Frequently Asked Questions (FAQ)

For more detailed information on common questions and setup details, please visit our [FAQ](./FAQ.md) section.

### Table of Contents

1. [Do I need to be whitelisted to run a miner node?](#1-do-i-need-to-be-whitelisted-to-run-a-miner-node)
2. [Why do I need to provide a private key when setting up a miner node?](#2-why-do-i-need-to-provide-a-private-key-when-setting-up-a-miner-node)
3. [How do I find my node's ID (formerly public\_key/peer\_id)?](#3-how-do-i-find-my-nodes-id-formerly-public_keypeer_id)
4. [I installed the validator, but I want to run a miner instead. What should I do?](#4-i-installed-the-validator-but-i-want-to-run-a-miner-instead-what-should-i-do)
5. [What’s the difference between a Distributed Miner and a Non-Distributed Miner?](#5-whats-the-difference-between-a-distributed-miner-and-a-non-distributed-miner)
6. [Why don't I see options to choose between distributed and non-distributed mining?](#6-why-dont-i-see-options-to-choose-between-distributed-and-non-distributed-mining)
7. [Can I run a miner node without a GPU?](#7-can-i-run-a-miner-node-without-a-gpu)
8. [How do I obtain a Hugging Face API key?](#8-how-do-i-obtain-a-hugging-face-api-key)
9. [Why don't I see the option to specify a model anymore?](#9-why-dont-i-see-the-option-to-specify-a-model-anymore)
10. [What is the difference between a miner and a validator?](#10-what-is-the-difference-between-a-miner-and-a-validator)
11. [What is the difference between Wizardry and Advanced Wizardry in the bootstrap script?](#11-what-is-the-difference-between-wizardry-and-advanced-wizardry-in-the-bootstrap-script)
12. [Is there current Windows support for running a miner?](#12-is-there-current-windows-support-for-running-a-miner)
13. [How does the referral system work?](#13-how-does-the-referral-system-work)

## Community and Support

If you need additional help or want to engage with the community, join the [Nesa Discord](https://discord.gg/nesa) for support and discussions. You can also explore more detailed documentation on the [Nesa GitBook](https://open.gitbook.com/~space/Vtjgh8wLtiRmdt9OTX2C/~gitbook/pdf).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details."# nesaa" 
