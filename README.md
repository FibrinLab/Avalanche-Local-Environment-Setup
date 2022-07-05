# Setting up your Development Environment for Local Subnet Development

## Introduction

Avalanche is an open-source platform for launching decentralized applications and enterprise blockchain deployments in one interoperable, highly scalable ecosystem. Avalanche is the first decentralized smart contracts platform built for the scale of global finance, with near-instant transaction finality. Avalanche is a blockchain that promises to combine scaling capabilities and quick confirmation times through its Avalanche Consensus Protocol. It can process 4,500 TPS (transactions per second). For Ethereum, that number is 14 TPS.

![avax](/images/1.jpeg "avax")

Blockchains have traditionally been referred to as being slow and unscalable. Avalanche embraces an innovative approach to concensus that solve these problems without compromising on security.

Avalanche is a high-performance, scalable, customizable, and secure blockchain platform. It targets three 15 broad use cases:

* Building application-specific blockchains, spanning permissioned (private) and permissionless (public)
deployments.
* Building and launching highly scalable and decentralized applications (Dapps).
* Building arbitrarily complex digital assets with custom rules, covenants, and riders (smart assets).

# Avalanche features 3 built-in blockchains: 
* Exchange Chain (X-Chain)
* Platform Chain (P-Chain)
* Contract Chain (C-Chain)

The P-chain is for platform management. It handles requests related to the validator, the subnet, and the blockchain. 
The C-chain is for contract management. It is based on EVM; hence its API is almost identical to other EVM protocols. It has both RPC and WebSocket endpoints, and it handles requests for smart contracts. 
The X-chain is for asset exchange. It is Avalanche’s native platform; it is used for creating and trading assets like AVAX and NFTs. 

These 3 blockchains are secured by the Avalanche Primary Network with is a special kind of subnet.

The Avalanche Architecture is composed of:
* Subnetworks
* Virtual Machines


## Prerequisites

### NodeJS and Yarn

First, install the LTS (long-term support) version of [nodejs](https://nodejs.org/en). This is `16.2.0` at the time of writing. NodeJS bundles `npm`.

Next, install the [yarn](https://yarnpkg.com) package manager:

```zsh
npm install -g yarn
```

### Git

To check the current Git version use:

```zsh
git --version
```


# Roadmap

This tutorial is created to serve as a guide to help developers setup their local environment for Avalanche subnet development. We are going to learn how to run a local network using the `avalanche-cli` and deploy a basic smart contract using `Remix` and `Hardhat`. This guide is an extension of the [Official Avalanche Documentation]().

Please note that all command line inputs and sample codes are MacOs and Linux Based. Commands may vary for other operating systems.

In summary, we will be discussing the following:
1. Running an EVM Subnet on the Local Network using the Avalanche-cli
2. Setting up metamask
3. Deploying smart contracts with Remix
4. Working with Hardhat


## 1. Running an EVM Subnet on the Local Network using the Avalanche-cli

We will be creating an EVM on our local machine to give us a basic feel on how a subnet functions. The [Avalanche-CLI](https://github.com/ava-labs/avalanche-cli) is a novel tool that allow up to have a local network up in minutes.


## Step 1: Installation

Open up you MacOs command line utility and run the following command

On your home directory, create a new and `cd <newdir>` into the directory. This is where we will be installing all our project dependencies.

```zsh
curl -sSfL https://raw.githubusercontent.com/ava-labs/avalanche-cli/main/scripts/install.sh | sh -s
```

This command download the latest binary of the [Avalanche-cli] to the current directory where it was executed.

`cd` into the `bin` folder and export the path variable

```zsh
cd bin
export PATH=$PWD:PATH
```

This makes the `avalanche` command available globally. For more information about [environment-variables]() and [avalanche-cli-commands]() visit the respective links.

![variables](/images/cover.jpeg "variables")


## Step 2: Initilizing a default subnet

We will be using the `avalanche subnet create` command line wizard to get our network running. STAT.
In the same directory where the binary was installed, run the following command

```zsh
avalanche subnet create <subnetName>
```
Substitute `<subnetName>` with any perferred name of your choice but without spaces. For this tutorial we are going to call our subnet `<fibrinNet>`.

```zsh
avalanche subnet create fibrinNet
```

Since this command does not provide any arguements, you would neeed to walk through the configuration wizard to generate a genesis file for your network.

* Choose a VM: 
  ![choose a VM](/images/2.png "Choose VM")
  We are going to be making use of the `SubnetEVM`

* Pick a chain ID
  ![chain ID](/images/3.png "Chain ID")
  Every EVM based blockchain has a special parameter called a `chainID`. ChainIDs are expected to be unique values, you can check [chainlist.org](https://chainlist.org/) to see if your proposed chain ID is already in use. We will be making use of the chain ID `1970` (A pun on JavaScript dates...lol).

* Select a symbol for the native subnet token
  ![symbol](/images/4.png "token symbol")

* Set fees: Select the `low disk use / low throughput` option
  ![fees](/images/5.png "fees")

* Airdrop: default to airdrop 1 million tokens to provided address
  ![airdrop](/images/6.png "airdrop")

* Add a custom precompile to modify the EVM: For this section, we will not be using a pre-compile script
  ![precompile](/images/7.png "precompile")


The wizard won't customize every aspect of the Subnet-EVM genesis for you, we will be doing this in the subsequent sections.

![complete](/images/8.png "complete")

To view the list of all created subnets, just execute the following command

```zsh
avalanche subnet list
```
![list](/images/9.png "list")


## Step 3: Deploying the Subnet Locally.

To deploy the newly created subnet locally, run the following command

```zsh
avalanche subnet deploy <subnetName>
```

![deploy](/images/10.png "deploy")

When a subnet is run locally, it starts a multi-node Avalanche Network in the background.

![deploy_f](/images/11.png "deploy_f")

To test the functionality of the just created subnet, go ahead and add the configuration details to [Metamask](https://metamask.io/).
You can create a new metamask account by importing the private key `0x56289e99c94b6912bfc12adc093c9b51124f0dc54ac7a766b2bc5ccf558d8027` and start experiencing with this account.

Lastly don't forget to stop the running local network
```zsh
avalanche network stop <snapshotName>
```

![deploy_f](/images/12.png "deploy_f")




# 2. Setting up metamask

Metamask is a cryptocurrency wallet used to interact with EVM based blockchains. It allows users to access their wallets through a browser extension which in turn can then be used to interact with decentralized apps.

## Step 1
In order to continue we would need to add the metamask extension to our web browser, in this case Google Chrome.
Follow the link below and follow the setup instructions to get metamask running.

[Install] Metamask.
The above link redirects you to the chrome web store.

![meta1](/images/20.png "meta1")

![meta2](/images/21.png "meta2")

`Please always verify` that the app is from the official source.

## Step 2

Click on the extension bar on the `top right` corner, you should get a pop-up that prompts you to set it up.

Next, we would need to create an account by setting up a `password`.

![meta3](/images/22.png "meta3")

The next step is the most important, `securing your just created account`.

Reveal the 12 word secret phrase and copy it down on a notebook. `It is a good idea not to back up this seed phrase digitally as it can be used to compromise your account`.

![meta4](/images/23.png "meta4")

Verify you secret phrase by inputing it again and you are done.

![meta5](/images/24.png "meta5")

## Step 3

Its now time to add the credentials of our newly created network into Metamask.

From the add-on pop-up, select the top right icon and click on `settings`

![meta6](/images/25.png "meta6")

![meta7](/images/26.png "meta7")


Switch to the `Network`  tab and `Add a network`

![meta8](/images/27.png "meta8")

Fill in the credentials of your just created subnet. Make sure the `RPC-URL` and `ChainID` are both correct. Also, input the currenty symbol and click on `done`

![meta9](/images/28.png "meta9")

This automatically imports the account where the tokens where deployed to, so you should have a balance of `1000000fib` tokens.

Hoooooray, you just go metamask setup.



# 3. Deploying smart contracts with Remix

## Step 1
We are going to be making use of an online IDE in compiling and deploying our smart contract code, a tool called [Remix](https://remix.ethereum.org/).
Remix, more commonly known as Remix IDE, is an open-source Ethereum IDE you can use to write, compile and debug Solidity code.

Navigate to the [Remix](https://remix.ethereum.org/) platform and select `import from github`. 

![remix1](/images/29.png "remix1")

![remix2](/images/30.png "remix2")


Paste the following link into the dialogue box.

![remix3](/images/31.png "remix3")

```zsh
https://github.com/FibrinLab/hello-world-1
```

This repo contains the a simple `Hello World` smart contract.

## Step 2
Compile and deploy the `Hello World` smart contract using the Local Subnet you just created. To do this select the `deploy` tab and choose `injected web3` from the dropdwown. `Please note that Remix automatically detects the appropriate compiler version and makes use of it to compile your contract.

![remix4](/images/32.png "remix5")

![remix6](/images/33.png "remix6")

`Always make sure to confirm the Environmet Chain ID is the same as that of your selected metamask account`.

Set the `string initMessage` to 
```zsh
"Hiya"
```
(with the quotes)

![deploy](/images/34.png "deploy")

With this all set go ahead and deploy your smart contract on your local subnet by clicking the `deploy` button. Approve the metamask request and pay the necessary gas fees.

If the the deployment is successful, you should see something like this ===>

![deploy2](/images/35.png "deploy2")


## Step 3: Interacting with our deployed instance.

You can query the Subnet the access the `message` variable by just simply clicking on the [Message] button. For this call, you would not require any gas fees.

![deploy3](/images/36.png "deploy3")

To update the `message` variable, simple type in the `newMessage` in the `string newMessage` field and select [update], approve the transaction any you are done. 

![deploy4](/images/37.png "deploy4")


# 4. Working with Hardhat

In this section we are going to be making use of [Hardhat] in writing, modifying and deploying our smart contract to our Local Subnet.



# Conclusion

Hooray, you made it to the end.
In this tutorial we have learnt how to get a Local Subnet up and running in minutes and deploy a simple smart contract to it. You have also been provided with a simple hardhat starter kit to help get you local environment setup quickly.

Feel free to fork this repo and happy coding.

Akanimoh Osutuk.