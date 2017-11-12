# [Nextflow](https://www.nextflow.io/) [Data-driven computational pipelines]
***
<2017.1110> by Colin Wu colinabc
## Get started
### Requirements
Nextflow can be used on any POSIX compatible system (Linux, Solaris, OS X, etc). It requires BASH and Java 8 or higher to be installed.

Windows systems may be supported using a POSIX compatibility layer like [Cygwin](http://www.cygwin.com/) (unverified) or in alternative installing it into a Linux VM using a virtualization software like [VirtualBox](http://www.virtualbox.org/) or [VMware](http://www.vmware.com/).

### Installation
*Nextflow* is distributed as a self-contained executable package, this means that it does not require any special installation procedure.

It only needs two easy steps:
1. Download the executable package by copying and pasting the following command in your terminal window: `wget -qO- get.nextflow.io | bash` or `curl -fsSL get.nextflow.io | bash`. It will create the `nextflow` main executable file in the current directory.

2. Optionally, move the `nextflow` file in a directory accessible by your `$PATH` variable (this is only required to avoid to remember and type the Nextflow full path each time you need to run it).