# K3s-node Terraform module

Terraform module for k3s cluster creation on a proxmox cluster

## Notes
- Artifacts directory is pre-populated with the install script.
- The k3s binary and airgap images tarball should be downloaded and placed in the artifacts directory of your terraform 
    - They must be specifically named
        - k3s-<arch>
        - k3s-airgap-images-<arch>.tar.zst