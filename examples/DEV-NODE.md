# Dev Node Example

`main.tf`
```
terraform {
  required_providers {
    proxmox = {
      source  = "telmate/proxmox"
      version = "2.9.10"
    }
  }
}

provider "proxmox" {
  pm_api_url      = "https://<proxmox IP or hostname>:8006/api2/json"
  pm_tls_insecure = false # set to true if certificates have not been setup
}


# prox Hosts
module "dev-test-1" {
  source = "github.com/brandtkeller/proxmox-terraform-modules//dev-node"

  name = "dev-test-1"
  boot = true
  pve_node = "prox" #proxmox node hostname
  clone_image  = "ubuntu-cloudimg-prox" # image template as described in the root readme

  storage_size = "100G"
  storage_type = "local-lvm"
  memory = 16384
  cpus = 4

  ip_addr = "192.168.1.61"
  nameservers = "8.8.8.8"
  password = var.password

}
```

`variables.tf`
```
variable "ssh_pub_key_path" {
  default = "~/.ssh/ssh.pub"
}

variable "ssh_priv_key_path" {
  default = "~/.ssh/ssh"
}

variable "password" {
  description = "vm user password"
  type        = string
  sensitive   = true
}
```

`bootstrap.sh`
```
#!/bin/bash

# kernel restart supression?
sudo sed -i "s/#\$nrconf{kernelhints} = -1;/\$nrconf{kernelhints} = -1;/g" /etc/needrestart/needrestart.conf
sudo sed -i "s/#\$nrconf{restart} = 'i';/\$nrconf{restart} = 'a';/g" /etc/needrestart/needrestart.conf

# # longhorn deps
# sudo apt install -y nfs-common
# sudo systemctl enable iscsid && sudo systemctl start iscsid
```