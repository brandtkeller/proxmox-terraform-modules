# proxmox-terraform-modules

Looking to abstract and host some terraform modules I use for my home Proxmox cluster.

## Goals
- Limit required external network traffic
    - Modules for kubernetes will likely focus on model around downloading the binary & airgap images once to the terraform execution host and then copying those to each VM created.   

## Cloud-Init
The VM image used for these modules is an Ubuntu cloudimg that has been configured for cloud-init on proxmox.

Feel free to use the provided [update script](./update.sh) from your proxmox host as a basis for configuring a template to use with the modules.

## Dependencies

### dev-node
When consuming this module - there is currently an expectation that a local `bootstrap.sh` is copied from the host executing the terraform to the target nodes. 

## Examples
- [dev-node](./examples/DEV-NODE.md)