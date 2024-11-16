# Frequently Asked Questions (FAQ)

## Table of Contents
- [Frequently Asked Questions (FAQ)](#frequently-asked-questions-faq)
  - [Table of Contents](#table-of-contents)
    - [1. Do I need to be whitelisted to run a miner node?](#1-do-i-need-to-be-whitelisted-to-run-a-miner-node)
    - [2. Why do I need to provide a private key when setting up a miner node?](#2-why-do-i-need-to-provide-a-private-key-when-setting-up-a-miner-node)
    - [3. How do I find my node's ID (formerly public\_key/peer\_id)?](#3-how-do-i-find-my-nodes-id-formerly-public_keypeer_id)
    - [4. I installed the validator, but I want to run a miner instead. What should I do?](#4-i-installed-the-validator-but-i-want-to-run-a-miner-instead-what-should-i-do)
    - [5. What’s the difference between a Distributed Miner and a Non-Distributed Miner?](#5-whats-the-difference-between-a-distributed-miner-and-a-non-distributed-miner)
    - [6. Why don't I see options to choose between distributed and non-distributed mining?](#6-why-dont-i-see-options-to-choose-between-distributed-and-non-distributed-mining)
    - [7. Can I run a miner node without a GPU?](#7-can-i-run-a-miner-node-without-a-gpu)
    - [8. How do I obtain a Hugging Face API key?](#8-how-do-i-obtain-a-hugging-face-api-key)
    - [9. Why don't I see the option to specify a model anymore?](#9-why-dont-i-see-the-option-to-specify-a-model-anymore)
    - [10. What is the difference between a miner and a validator?](#10-what-is-the-difference-between-a-miner-and-a-validator)
    - [11. What is the difference between Wizardry and Advanced Wizardry in the bootstrap script?](#11-what-is-the-difference-between-wizardry-and-advanced-wizardry-in-the-bootstrap-script)
    - [12. Is there current Windows support for running a miner?](#12-is-there-current-windows-support-for-running-a-miner)
    - [13. How does the referral system work?](#13-how-does-the-referral-system-work)

### 1. Do I need to be whitelisted to run a miner node?
No, you do not need to be whitelisted to run a miner node. Anyone can participate as a miner on the Nesa network. However, being whitelisted can make it easier to obtain your Nesa wallet private key, which is used when setting up your miner. We recommend using [Leap Wallet](https://www.leapwallet.io/) to obtain your private key, as Keplr does not allow private key export unless it was imported as a private key. Simply follow the guide provided in the documentation to get started.

You don't have to have Nesa's testnet configured on leap to get your private key. You can simply create a new wallet and export the private key. Refer to this section of the documentation if you want to setup your wallet for the testnet, [Step 3: Configure Nesa Chain](https://docs.nesa.ai/nesa/using-nesa/getting-started/wallet-setup#step-3-configure-nesa-chain). This section is wallet agnostic and will work with any wallet that supports the Nesa chain.

### 2. Why do I need to provide a private key when setting up a miner node?

The private key serves several important functions in the Nesa network:

1. **Node Authentication**: It's used to securely identify and authenticate your node on the network.
2. **Transaction Signing**: On the mainnet, it will be used to sign transactions, including registering your node and receiving rewards.
3. **Reward Distribution**: It associates your node with your wallet, ensuring that you receive rewards for your contributions to the network.

While some of these functions are not fully utilized on the testnet, including the private key now prepares your node for seamless transition to the mainnet. It also allows us to accurately track contributions and allocate testnet rewards, which will be used to distribute mainnet NES tokens to active testnet participants after the Token Generation Event (TGE).

By providing your private key during setup, you're ensuring that your node is fully prepared for both current testnet operations and future mainnet functionality.

### 3. How do I find my node's ID (formerly public_key/peer_id)?
Re-run the bootstrap script in advanced mode, and check the header for your node ID and dashboard link. This ID is used by our networking stack and for rewards on the testnet. It can be found in the header of the bootstrap script and the last prompt where it shows the entire config before bootstrapping your node. There is also a link directly to your node's dashboard, but you can also visit [https://nodes.nesa.ai](https://nodes.nesa.ai) and search for your node by its node ID.

The following image shows the node id in the header of the bootstrap script, and the node id in both the header and the config preview presented before finalizing the bootstrapping process. ![Node ID in the bootstrap script](https://raw.githubusercontent.com/nesaorg/bootstrap/master/images/node_id.png)

### 4. I installed the validator, but I want to run a miner instead. What should I do?
Currently, we are not onboarding validators. We recommend focusing on running a miner instead. Re-run the bootstrap script, select the miner option, and ensure that you only select miner.

### 5. What’s the difference between a Distributed Miner and a Non-Distributed Miner?
Luckily, you no longer have to concern yourself with this. This is handled by the network based on miner resources. However, here is a brief explanation of the two types:

- **Distributed Miner:** Joins existing swarms for collaborative mining, splitting the model into blocks and running inference on a sequence of miners. You can either join an existing swarm or start a new one.
- **Non-Distributed Miner:** Operates independently without collaboration, running the entire model on a single machine. This option has fewer moving parts, but you must choose a model that fits your hardware specifications.

### 6. Why don't I see options to choose between distributed and non-distributed mining?
To simplify the setup process for community members, we've streamlined the node configuration. The network now handles the distribution of tasks internally, optimizing for efficiency without requiring user input on these technical details.

### 7. Can I run a miner node without a GPU?
Yes, you can run a miner node without a GPU. The node will primarily rely on your CPU and RAM for processing. Currently, we support CUDA, MPS, and CPU backends, so you have flexibility depending on your hardware setup.

### 8. How do I obtain a Hugging Face API key?
To obtain a Hugging Face API key, follow these steps:
1. Visit the [Hugging Face website](https://huggingface.co/).
2. Sign up or log in to your account.
3. Navigate to your [API tokens page](https://huggingface.co/settings/tokens) under your account settings.
4. Click “New token” to generate an API key.
5. Copy the generated key and use it in your miner configuration.

### 9. Why don't I see the option to specify a model anymore?
We've simplified the setup process for community members to focus on network health and optimization. Instead of individual miners choosing specific models, the network now automatically balances and distributes tasks based on overall network needs and individual node capabilities. This approach allows us to:
- Optimize network performance by efficiently allocating resources.
- Ensure a balanced distribution of tasks across all miners.
- Simplify the setup process for users, reducing potential configuration errors.
- Adapt quickly to changing network demands and model requirements.

Rest assured that your node will be utilized effectively, contributing to the overall health and performance of the Nesa network.

### 10. What is the difference between a miner and a validator?
- **Miners**: On the Nesa network, miners perform inference tasks using their computing power. They process data and run models, contributing directly to the network's AI operations. Miners earn rewards based on their contributions to these tasks. Miners are focused on providing computational power to run AI models.
- **Validators**: Validators help secure the network by participating in consensus, committing new blocks to the blockchain, and voting on proposals. They ensure that the network operates correctly and securely. Validators are crucial for maintaining the integrity of the blockchain, and they are selected based on specific criteria, including their ability to stake coins and their participation in governance.

### 11. What is the difference between Wizardry and Advanced Wizardry in the bootstrap script?
- **Wizardry**: This is the standard setup mode where the script walks you through the configuration process step-by-step, prompting you for inputs where necessary. It's designed to guide you through the installation with minimal complexity.
- **Advanced Wizardry**: This mode is intended for more advanced users who might want to set up multiple nodes or customize specific configurations beyond the standard options. It allows you to pre-configure settings in one go, manually set variables that aren't customizable in the regular wizardry mode, and skip the wizardry prompts if you’ve already set up your configuration previously.

### 12. Is there current Windows support for running a miner?
Yes, there is support for running a miner on Windows. Follow the guide in the documentation to get started. Ensure you have Docker Desktop installed with WSL 2 enabled and run the bootstrap script as instructed.

### 13. How does the referral system work?
When setting up your node, you have the option to enter a referral code. This code is the public key of the person who referred you to the Nesa network. While optional, providing a valid referral code will offer benefits to both you and the referrer. The specific details will be announced soon.