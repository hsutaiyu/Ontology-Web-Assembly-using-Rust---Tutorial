---
description: Setting up the required tools on the local machine
---

# Development Environment

To make the development process as smooth and as efficient as possible, we recommend confirming that all the tools mentioned below are installed and configured properly on your local machine.

* **Rust** development environment
* An **Integrated Development Environment** \(IDE\) software
* Ontology's **WASM** contract testing **private node** 

Let us look at the installation process for the above mentioned tools one by one.

{% hint style="warning" %}
For this tutorial, we will be setting up a private test node for testing our `WASM` contract. This will allows us to add `debug` information to the contract and monitor the contract's run-time information in the logs section. In case you feel that node setup is complicated, you can always use the `test net` to deploy and invoke contracts, something that we are working on at Ontology and hope to make available very soon.
{% endhint %}

## Rust Development Environment

**Non-windows** platforms can use the following shell command to install `rustup`.

```bash
curl https://sh.rustup.rs -sSf | sh
```

For **windows** users, please follow [this](https://www.rust-lang.org/tools/install) link to directly download `rustup` from the official website. Install and add the respective `PATH` environment variables by following the directions provided.

Install the `rust` compiler using this shell command.

```bash
rustup install nightly
```

Set the default compiler version to nightly by-

```bash
rustup default nightly
```

Install the `wasm32` compiler target-

```bash
rustup target add wasm32-unknown-unknown
```

Later when we write our `rust` code, we will be compiling it and converting it to bytecode using the `cargo` tool. But, the file that `cargo` generates is relatively large in size. Therefore, to compress the bytecode file, as well as to check and optimize it for deploying on the blockchain, we will be using the `ontio-wasm-build` tool.

`ontio-wasm-build` can be installed using the following shell commands-

```bash
git clone https://github.com/ontio/ontio-wasm-build
cd ontio-wasm-build
cargo build --release
```

For more details on `ontio-wasm-build`, please refer to [this](https://github.com/ontio/ontio-wasm-build) link.

## Integrated Development Environment \(IDE\) Software

Since we will be using rust, there are certain `IDEs` that work well. The following `IDEs` can be used-

* _**IntelliJ IDEA**_ - [https://www.jetbrains.com/idea/download](https://www.jetbrains.com/idea/download)
* _**IntelliJ CLion**_ - [https://www.jetbrains.com/clion/download/](https://www.jetbrains.com/clion/download/)
* _**Vim Editor**_ - [https://www.vim.org/download.php](https://www.vim.org/download.php)

## Local Test Node Set-up

A private node can be set up on the local machine and run using Ontology's `CLI`.

In order to realize this, we must first download and configure the implementation of Ontology's core software. 

{% hint style="info" %}
Information and direction on how to build Ontology from the source code can be found by following [this](https://github.com/ontio/ontology#build-from-source-code) link.
{% endhint %}

The executable for the latest release different operating systems can be downloaded from [this](https://github.com/ontio/ontology/releases/) link.

After download and installing Ontology, we don't have to build it from the source code and can directly proceed with the development process. 

{% hint style="warning" %}
When running the pre-built executable file, please set the log level to "DEBUG" mode. Debug information is more conveniently accessible in this mode.
{% endhint %}



