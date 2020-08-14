# Vagrant Support

Packer build templates are provided to build Vagrant boxes locally or to build and publish a Vagrant box on [Vagrant Cloud](https://app.vagrantup.com).

## Setup

- Install [Vagrant](https://vagrantup.com).
- Run `packer build alpine.json` to build the OVA.
- Import the generated OVA into VirtualBox.

## Local Vagrant box

From the `vagrant` directory run `packer build vagrant.json`

You can then use vagrant commands to add, init, and run the box.

## Vagrant Cloud

### Prerequisites

- You will need a Vagrant Cloud account.
- You will need to generate an [authentication token](https://www.vagrantup.com/vagrant-cloud/users/authentication).
- You will need to create a Box entry on Vagrant Cloud that will host the published box versions.

### Building and Publishing

- Set the environment variable `VC_TOKEN` to your Vagrant Cloud access token.
- Edit vagrant-cloud.json and update `box_tag` to match your Vagrant Cloud account name and box name.
- Edit `box_version` and set a unique version number.
- From the `vagrant` directory run `packer build vagrant-cloud.json`.

The published box is available with the following commands:

```bash
vagrant init <box_tag> \
  --box-version <box_version>
vagrant up
```
