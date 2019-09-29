---
description: Writing your smart contract from scratch
---

# Creating your own project

Using templates is convenient but it might limit certain dimensions of the development process. 

So, let us write a contract from scratch and test it. This will be more helpful for developers who are familiar with smart contract development but are just getting started with Ontology `WASM` smart contracts.

## Create a new smart contract

We create a new library, so to speak, to start implementing a new smart contract. Navigate to the appropriate directory and execute the following code-

```bash
cargo new --lib helloworld
```

If successfully executed, the file hierarchy of the new library would look like so-

```bash
.
├── Cargo.toml
└── src
    └── lib.rs
```

As you may have noticed, a rust based `WASM` contract consists of two components, one being the `Cargo.toml` file and the other being the `src/lib.rs` rust file that is used to write and implement contract logic.

## Generate the ontio-std API file

Before generating the API file, we need to edit the `Cargo.toml` file to add certain dependencies and libraries that will be used later.

First, under the `[dependencies]` configuration, include the Ontology `WASM` contract toolkit. Also, since we will compiling the contract in a form that is different from the standard, we need to add `[lib]` configuration settings. 

The `[features]` configuration is used to toggle certain unstable features. Please not that these features can only be compiled using the nightly compiler. 

A complete `Cargo.toml` would look something like-

```yaml
[package]
name = "helloworld"
version = "0.1.0"
authors = ["Lucas <sishsh@163.com>"]
edition = "2018"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html
[lib]
crate-type = ["cdylib"]
path = "src/lib.rs"
[dependencies]
ontio-std = {git="https://github.com/ontio/ontology-wasm-cdt-rust.git"}

[features]
mock = ["ontio-std/mock"]
```

We still do not know the `APIs` that we can use from the toolkit that we just included in the project dependencies.

The following command can be used to generate the `API` documentation for this library.

```bash
cargo doc
```

After successful execution of the above command the project structure would be as follows-

```bash
.
├── Cargo.lock
├── Cargo.toml
├── src
│   └── lib.rs
└── target
    ├── debug
    └── doc
```

The API documentation can be found in the `doc` directory. The `settings.html` file can be opened using a web browser. The reference for `ontio-std` library looks like-

![](.gitbook/assets/wasm-doc-ontiostd.jpg)

{% hint style="warning" %}
Libraries are referred to as **crates** in the context of `Rust`.
{% endhint %}

