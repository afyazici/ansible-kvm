# KVM Provisioning with Ansible

This repository contains Ansible roles and playbooks for provisioning virtual machines (VMs) on KVM (Kernel-based Virtual Machine) hypervisor. With these Ansible scripts, you can easily deploy VMs based on cloud images with customizable configurations.

## Prerequisites

Before running the Ansible playbooks, ensure that the following prerequisites are met:

- Ansible is installed on the control machine.
- Required packages (`guestfs-tools` and `python3-libvirt`) are installed on the control machine.
- Access to the KVM hypervisor.
- Necessary permissions to create and manage VMs.

## Usage

1. Clone this repository to your local machine:

    ```bash
    git clone <repository-url>
    ```

2. Modify the configuration variables according to your requirements. The main configuration files are:
    - `kvm.yml`: This playbook defines tasks for deploying VMs based on cloud images.
    - `roles/kvm_provision/defaults/main.yml`: Default variables for VM provisioning such as VM names, CPU, RAM, network configuration, etc.
    - `roles/kvm_provision/tasks/main.yml`: Tasks for ensuring prerequisites and creating VMs.
    - `roles/kvm_provision/templates/vm-template.xml.j2`: XML template for defining VM configurations.

3. Run the playbook `kvm.yml`:

    ```bash
    ansible-playbook kvm.yml
    ```

## Configuration Details

- **kvm.yml**: This playbook contains tasks for deploying VMs based on cloud images. It includes roles for KVM provisioning.
- **roles/kvm_provision/defaults/main.yml**: This file defines default variables used in KVM provisioning. You can customize VM names, CPU, RAM, network configuration, SSH keys, and other parameters here.
- **roles/kvm_provision/tasks/main.yml**: Tasks file for KVM provisioning. It includes tasks for ensuring required packages are installed, getting a list of existing VMs, creating VMs, and cleaning up temporary files.
- **roles/kvm_provision/templates/vm-template.xml.j2**: This Jinja2 template file defines the XML configuration for VMs. It includes settings for memory, CPU, disks, network interfaces, graphics, and other devices.

## Customization

- Modify `roles/kvm_provision/defaults/main.yml` to change default VM configurations.
- Update `roles/kvm_provision/templates/vm-template.xml.j2` for customizing VM settings such as disk size, CPU model, etc.
- Adjust playbook `kvm.yml` if additional tasks or roles are required.

## Contributors

@c3ng0

## License

This project is licensed under the MIT License.
