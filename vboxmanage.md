# Basic VM Operations

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage list vms`                                      | Lists all registered VMs by name and UUID.                     |
| `VBoxManage startvm "<VM Name>"`                           | Starts a VM with the specified name or UUID in headless mode.  |
| `VBoxManage controlvm "<VM Name>" poweroff`                | Forces a VM to power off (similar to pulling the plug).        |
| `VBoxManage controlvm "<VM Name>" acpipowerbutton`         | Sends an ACPI shutdown signal (graceful shutdown).             |
| `VBoxManage controlvm "<VM Name>" reset`                   | Resets (reboots) a running VM.                                 |
| `VBoxManage controlvm "<VM Name>" pause`                   | Pauses a running VM.                                           |
| `VBoxManage controlvm "<VM Name>" resume`                  | Resumes a paused VM.                                           |

# Creating and Cloning VMs

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage createvm --name "<VM Name>" --register`        | Creates a new virtual machine.                                 |
| `VBoxManage clonevm "<Source VM Name>" --name "<New VM Name>" --register` | Clones an existing VM.                     |
| `VBoxManage unregistervm "<VM Name>" --delete`             | Unregisters and deletes a VM.                                  |

# Modifying VM Configuration

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage modifyvm "<VM Name>" --memory <Size in MB>`    | Sets the amount of RAM allocated to a VM.                      |
| `VBoxManage modifyvm "<VM Name>" --cpus <Number of CPUs>`  | Sets the number of CPUs assigned to the VM.                    |
| `VBoxManage modifyvm "<VM Name>" --nic<N> nat`             | Sets the network interface card `<N>` to use NAT mode.         |
| `VBoxManage modifyvm "<VM Name>" --audio none`             | Disables audio for the VM.                                     |
| `VBoxManage modifyvm "<VM Name>" --vrde on`                | Enables VRDP (Remote Desktop Protocol) access to the VM.       |
| `VBoxManage modifyvm "<VM Name>" --ostype <OS Type>`       | Sets the OS type (e.g., "Ubuntu_64" or "Windows10_64").        |

# Disk and Storage Management

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage createmedium disk --filename "<Path>" --size <Size in MB>` | Creates a new virtual disk with the specified size.         |
| `VBoxManage storagectl "<VM Name>" --name "<Controller Name>" --add sata` | Adds a new SATA controller to a VM.                      |
| `VBoxManage storageattach "<VM Name>" --storagectl "<Controller Name>" --port 0 --device 0 --type hdd --medium "<Path to Disk>"` | Attaches a virtual disk to a VM.  |

# Snapshots

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage snapshot "<VM Name>" take "<Snapshot Name>"`   | Takes a snapshot of the current state of a VM.                 |
| `VBoxManage snapshot "<VM Name>" list`                     | Lists all snapshots of a VM.                                   |
| `VBoxManage snapshot "<VM Name>" restore "<Snapshot Name>"`| Restores the VM to a specified snapshot.                       |

# Network Configuration

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage modifyvm "<VM Name>" --nic<N> bridged --bridgeadapter<N> "<Adapter>"` | Configures network adapter `<N>` to use bridged mode.         |
| `VBoxManage modifyvm "<VM Name>" --nic<N> natnetwork "<NatNetworkName>"` | Attaches a VM to a named NAT network.                  |
| `VBoxManage natnetwork add --netname "<NatNetworkName>" --network "<CIDR>" --enable` | Creates and enables a new NAT network with the specified CIDR. |

# VRDP (Remote Desktop) Configuration

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage modifyvm "<VM Name>" --vrdeport <Port>`        | Sets the VRDP port (default is 3389).                          |
| `VBoxManage modifyvm "<VM Name>" --vrde on`                | Enables VRDP.                                                  |

# VM Information

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage showvminfo "<VM Name>"`                        | Displays detailed information about a VM.                      |
| `VBoxManage list runningvms`                               | Lists all currently running VMs.                               |
| `VBoxManage guestproperty get "<VM Name>" "/VirtualBox/GuestInfo/Net/0/V4/IP"` | Gets the guest IP address.                  |

# Miscellaneous

| Command                                                   | Description                                                    |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `VBoxManage list hostinfo`                                 | Lists information about the host system.                       |
| `VBoxManage list bridgedifs`                               | Lists available bridged network interfaces.                    |
| `VBoxManage list natnets`                                  | Lists configured NAT networks.                                 |
| `VBoxManage extpack install "<Path to Extension Pack>"`    | Installs a VirtualBox extension pack.                          |
