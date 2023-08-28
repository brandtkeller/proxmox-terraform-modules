# K3s-node Terraform module

Terraform module for k3s cluster creation on a proxmox cluster

## Dependencies

### artifacts
- This module requires you to have the artifacts required for airgap k3s downloaded and in an `artifacts/` directory with your `main.tf`
- This module requires you to have a `bootstrap.sh` file in the directory with your `main.tf`
    - This is for any additional modification you want to make to the node directly

## Notes
- Artifacts directory is pre-populated with the install script.
- The k3s binary and airgap images tarball should be downloaded and placed in the artifacts directory of your terraform 
    - They must be specifically named
        - k3s-<arch>
        - k3s-airgap-images-<arch>.tar.zst

## Example directory
```
├── artifacts
│   ├── k3s-airgap-images-amd64.tar.zst
│   └── k3s-amd64
├── bootstrap.sh
├── main.tf
└── variables.tf
```