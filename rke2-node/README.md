# Rke2-node Terraform module

Terraform module for rke2 cluster creation on a proxmox cluster

## Dependencies

### artifacts
- This module requires you to have the artifacts required for airgap rke2 downloaded and in an `artifacts/` directory with your `main.tf`
- This module requires you to have a `bootstrap.sh` file in the directory with your `main.tf`
    - This is for any additional modification you want to make to the node directly

## Notes
- Artifacts directory is pre-populated with the install script.
- The rke2 binary tarball, airgap images tarball, and the shasum text file for the images should be downloaded and placed in the artifacts directory of your terraform.

## Example directory
```
├── artifacts
│   ├── rke2-images.linux-amd64.tar.zst
│   ├── rke2.linux-amd64.tar.gz
│   └── sha256sum-amd64.txt
├── bootstrap.sh
├── main.tf
└── variables.tf
```