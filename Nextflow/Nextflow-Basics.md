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

### Your first script: `tutorial.nf`
```
#!/usr/bin/env nextflow

params.str = 'Hello world!'

process splitLetters {

    output:
    file 'chunk_*' into letters mode flatten

    """
    printf '${params.str}' | split -b 6 - chunk_
    """
}

process convertToUpper {

    input:
    file x from letters

    output:
    stdout result

    """
    cat $x | tr '[a-z]' '[A-Z]'
    """
}

result.subscribe {
    println it.trim()
}
```
> This script is made up of two processes, the first splits a string in file chunks containing 6 characters, the following process receives these files and transform the content to uppercase letters. The resulting strings are emitted on the `result` channel and finally the output is printed out by the `subscribe` operator.

Execution: `nextflow run tutorial.nf`

Outputs:
```
N E X T F L O W  ~  version 0.9.0
[warm up] executor > local
[22/7548fa] Submitted process > splitLetters (1)
[e2/008ee9] Submitted process > convertToUpper (1)
[1e/165130] Submitted process > convertToUpper (2)
HELLO
WORLD!
```
> The hexadecimal numbers, like `22/7548fa`, identify the unique process execution. These numbers are also the prefix of the directories where each process is executed. You can inspect the files produced by them changing to the directory `$PWD/work` and using that numbers to find the process specific execution path.

### Modify and resume 
Nextflow keep track of all the processes executed in your pipeline. If you modify some parts of your script, only the processes that are actually changed will be re-executed. The execution of the processes that are not changed will be skipped and the cached result used instead.

This helps a lot when testing or modifying part of your pipeline without having to re-execute it from scratch.

Modify the script and execute it: `nextflow run tutorial.nf -resume`

The process with process ID as before means it is actually skipped.

> The pipeline results are cached by default in the directory `$PWD/work`. Depending your script this folder can take of lot of disk space. If your are sure you won't resume your pipeline execution, clean this folder periodically.

### Pipeline parameter 
Pipeline parameters are simply declared by pre-pending to a variable name the prefix `params` separated by dot character. Their value can be specified on the command line by prefixing the parameter name with a double dash character, i.e. `--paramName`

For the sake of this tutorial you can try to execute the previous example specifying a different input string parameter, as shown below:

```
nextflow run tutorial.nf --str 'Hola mundo'
```

## Basic concepts
Nextflow is a reactive workflow framework and a programming [DSL](http://en.wikipedia.org/wiki/Domain-specific_language) that eases the writing of computational pipelines with complex data.

It is designed around the idea that the Linux platform is the [lingua franca](通用语) of data science. Linux provides many simple command line and scripting tools, which by themselves are powerful, but when chained together facilitate complex data manipulations.

*Nextflow* extends this approach adding to it the ability to define complex program interactions and an high-level parallel computational environment based on the *dataflow* programming model.

### Processes and channels
In practice a Nextflow pipeline script is made by joining together many different processes. Each process can be written in any scripting language that can be executed by the Linux platform (BASH, Perl, Ruby, Python, etc).

Processes are executed independently and are isolated from each other i.e. they do not share a common (writable) state. The only way they can communicate is by using asynchronous FIFO queues, called *channels* in the Nextflow lingo.

Any process can define one or more channels as input and output. The interaction between these processes, and ultimately the pipeline execution flow itself, is implicitly defined by these input and output declarations.

A Nextflow script looks like the following example:
```
params.query = "$HOME/sample.fa"
params.db = "$HOME/tools/blast-db/pdb/pdb"

db = file(params.db)
query = file(params.query)

process blastSearch {
    input:
    file query

    output:
    file top_hits

    """
    blastp -db $db -query $query -outfmt 6 > blast_result
    cat blast_result | head -n 10 | cut -f 2 > top_hits
    """
}


process extractTopHits {
    input:
    file top_hits

    output:
    file sequences

    """
    blastdbcmd -db ${db} -entry_batch $top_hits > sequences
    """
}
```
> In the above example two processes are defined. The execution order is not set by the fact that `blastSearch` process comes before the `extractTopHits` in the script (it could also be written the other way around) but because the first defines the channel `top_hits` in its output declarations while the `extractTopHits` process defines the same channel in its input declaration, and thus establishing a communication link from the blastSearch task towards the *extractTopHits* task.

Read [Channel](#3) and [Process](#2) sections to learn more about these features.

### Execution abstraction 
While a process defines *what* command or script has to be executed, the executor has the role to determine *how* that script is actually run in the target system.

If not specified otherwise processes are executed in the local computer. The local executor is very useful for pipeline development and test purposes, but for real world computational pipelines, an HPC or cloud platform is required.

In other words, *Nextflow* provides an abstraction between the pipeline's functional logic and the underlying execution system. Thus it is possible to write a pipeline once and have it running on your computer, a grid platform or the cloud seamlessly, without modifying it, by simply defining the target execution platform in the configuration file.

The following HPC and cloud platforms are supported:

- [Open grid engine](http://gridscheduler.sourceforge.net/)
- [Univa grid engine](http://www.univa.com/)
- [Platform LSF](http://www.ibm.com/systems/technicalcomputing/platformcomputing/products/lsf/)
- [Linux SLURM](https://computing.llnl.gov/linux/slurm/)
- [PBS Works](http://www.pbsworks.com/gridengine/)
- [Torque](http://www.adaptivecomputing.com/products/open-source/torque/)
- [HTCondor](https://research.cs.wisc.edu/htcondor/)

Read [Executors](#4) section to learn more about Nextflow executors.

### Scripting language 
Although *Nextflow* is designed to be used with a minimal learning curve, without having to study a new programming language and using your current skills, it also provides a powerful DSL scripting language.

Nextflow scripting is an extension of the [Groovy programming language](http://en.wikipedia.org/wiki/Groovy) which in turn is a super-set of the Java programming language, thus if you have some knowledge of these languages, or even only some confidence with the *C/C++* syntax, you will be comfortable using it.

Read [Pipeline script](#1) section to learn about Nextflow scripting language.

### Configuration options
Pipeline configuration properties are defined in a file named `nextflow.config` in the pipeline execution directory.

It allows to set what executor to use, the processes environment variables, pipeline parameters etc.

A basic configuration file looks like the following example:
```
process {
  executor='sge'
  queue = 'cn-el6'
}

env {
  PATH="$PWD/bowtie2:$PWD/tophat2:$PATH"
}
```
Read [Configuration](#5) section to learn more about the Nextflow configuration file and settings.

## Examples



