# CentOS Kernel-based Virtual Machine (KVM)

Ansible role to deploy a CentOS Virtual Machine on your local Linux system using KVM (Kernel-based Virtual Machine).

## Usage

#### 1. Install the required dependencies to run KVM.

```bash
$ ansible-playbook 00_hv_install.yml
```

<details>
    <summary>Click here to see the list of packages</summary>
    
* **qemu-kvm** – Provides hardware emulation.
* **libvirt-daemon-system** – Configuration files required to run the libvirt daemon.
* **libvirt-clients** – Client-side libraries and APIs for managing and controlling virtual machines & hypervisors from the command line.
* **virtinst** – A  set of command-line utilities for provisioning and modifying virtual machines.
* **virt-manager** – A Qt-based graphical interface for managing virtual machines via the libvirt daemon.
* **bridge-utils** – A set of tools for creating and managing bridge devices.
* **cpu-checker** – To check whether your system is cabable of of running hardware accelerated KVM virtual machines (run ```kvm-ok``` from the cmd)
</details>

#### 2. Set the Virtual Machine properties.

Edit ```01_guest_install.yml``` and set the following variables:
* **vm_base_image_version** - CentOS image version
* **vm_template** - CentOS cloud image in qcow2 file format (List of available versions [here](https://cloud.centos.org/centos/7/images/))
* **guest_root_password** - Root user password
* **guest_name** - Virtual Machine name
* **guest_ram** - Amount of RAM (KiB) for the Virtual Machine 
* **guest_cpus** - Amount of CPU cores for the Virtual Machine

Deploy the Virtual Machine.

```bash
$ ansible-playbook 01_guest_install.yml
```

#### 3. Access the Virtual Machine.

Open the Virtual Machine Manager (provided by the ```virt-manager``` package) to see the newly deployed Virtual Machine.

![vmm](https://github.com/barrigas/centos_qcow2/blob/main/images/vmm.png)

Check the assigned IP address.

![vm-1](https://github.com/barrigas/centos_qcow2/blob/main/images/vm-1.png)

[Optional] Access the Virtual Machine from your terminal emulator.

```bash
$ ssh root@192.168.122.12
```
