# Setting up an IOTA full-node on an SBC (Single-board computer)

#### Warning: 
Ths guide uses cIRI. This project is still a work in progress. Do not except a stable full-node at the moment.
Do not use this guide to setup a production ready full-node.
cIRI does not support

This guide describes how to setup a full-node on a small SBC. Since SBCs usually have restricted resources, 
we decided to recommend and use cIRI for the setup. CIRI is designed to be more efficient than IRI, but it might not
contain the most recent features or extensions. So, if you want to adapt the newest features & extensions, you might 
want to use IRI instead. IRI requires 4 GB of memory, so you only have a few SBCs where IRI works reliable and fast. 

*_Note:_* I use an Orange Pi Zero & Zero Plus for this guide, but I try to keep it as general as possible.
So, it should be possible to follow it with any common ARM based SBC.
I cover ARMv7 & ARMv8A (32-Bit & 64-Bit). So you should be able to run this guide on any Cortex-A platform.

Host system requirements:

- Linux based host system. (Ubuntu is used in this guide) MacOS should also work.
Note: If you use Windows, you should use [a Linux VM.](https://www.windowscentral.com/how-run-linux-distros-windows-10-using-hyper-v)
Windows 10 also supports the [Linux Subsystem.](https://docs.microsoft.com/en-us/windows/wsl/install-win10) 
With it you are able to run Linux without the overhead of a VM.
If you are an advanced user, you can also replace the Linux tools with the Windows equivalent.

SBC requirements:

- Ubuntu (or other Linux based OS, BSD might also work) with enabled SSH & configured network
*_Note:_* You might want to check our "Setting up an SBC for IOTA guide"

- At least 256 MB memory. Better: 512 MB or 1 GB. 
*_Note:_* It is recommended to disable PoW for small SBCs. 
Outsourcing the workload to a faster server might be also a good option for small SBCs.

- Ubuntu (Other Linux distribution should also work. BSD based OS might also work.) 
*_Note:_* The guide uses Ubuntu. We recommend to stick to Ubuntu if you consider yourself as beginner

- At least 16 GB storage (for testing purposes), to run the main-tangle: at least 64 GB.


## Clone the git repository

```bash
git clone https://github.com/iotaledger/entangled.git
```

## Install Bazel

Follow the [installation guide](https://docs.bazel.build/versions/master/install.html) for your OS in the Bazel documentation.

## Cross compile cIRI

### ARMv8 (64-Bit)

```bash
cd ent
bazel build -c opt --define network=mainnet --define trit_encoding=5 --crosstool_top=@iota_toolchains//tools/aarch64--glibc--bleeding-edge-2018.07-1:toolchain --cpu=aarch64 --compiler='gcc' --host_crosstool_top=@bazel_tools//tools/cpp:toolchain //ciri
```