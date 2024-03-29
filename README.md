# LXC/MOLECULE PLATFORM FOR PLAYBOOK AND ROLE TESTING WITH ANSIBLE

This is an Ansible role that creates two LXC containers on your local machine. Once deployed, you can run any playbooks or roles against these instances.

**WHY LXC**

LXC offers the best of both worlds between containers and virtual machines (VMs). On one hand, they are lightweight and can be spun up in seconds. On the other hand, you get a full OS environment that allows you to test system service configurations and much more than what is possible with a Docker/Podman container.

The molecule configuration in "molecule/default/molecule.yml" starts up an Ubuntu 22.04 and a CentOS 8 Stream LXC instance. Customize it to fit your needs.

**Both Kubernetes and K3s are fully supported.**

## Requirements

**System:**

Linux OS with LXD Linux system container and virtual machine manager installed

At least 8GB of RAM

Minimum 4 CPU cores

**Packages**:

Ansible, pip3, molecule-lxc, ansible-lint, yamllint

## Role Variables

**new_user_passwd:** Set a password for the "admin" user which can be used to

login to the the instance. Use "genpass" to generate a base 64 encoded string.

```
./genpass

```

**perso_pubkey:** Public SSH key to be inserted into the instance for

passwordless login.

**pub_key_user:** Username which be created and granted sudo privileges.

Edit "defaults/main.yml" to assign these values.

## Example

```
molecule converge

```

Is all you need to get up and running.

The "default_profile.yml" can be used as a reference for adding limitations

```
lxc profile edit default

```

To make changes.

```
lxc list

```

Will show the status of your instances.

See LXC and LXD documentation or run:

```
./cheat lxc

./cheat molecule

```

**To get the basics**

At this stage you should be able to add these containers IP addresses to an inventory

and run playbooks against them.

## License

GPLv3

## Author Information

Name: Michael Nelson

LET'S GET IT AUTOMATED AND BE LAZY :<)
