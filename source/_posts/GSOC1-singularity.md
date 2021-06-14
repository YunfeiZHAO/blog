---
title: GSOC week1 - Singularity - (May 24, 2021 - May 30, 2021)
date: 2021-05-30 12:13:53
category: GSOC 2021 Redhen
tags: [HPC]
excerpt: 'Community bonding period with Redhen during Google Summer of Code 2021. An introduction to Singularity and setup Singularity on HPC.
(May 24, 2021 - May 30, 2021)'

index_img: /img/singularity/singularity.png
banner_img: /img/GSOC_2021/gsoc2021.png
comment: disqus
---
# Introduction of Singularity
During GSOC 2021 with Redhen, We have access to The High Performance Computing Clusters located at ["CWRU"](https://case.edu/utech/departments/research-computing) that represents Case Western Reserve University. We need to have our final result run in a Singularity container on this HPC. I used Docker before, and this time I want to make an introduction to Singularity.
Before starting reading this article, I will recommand you with two resouces.
["Singularity Github"](https://github.com/hpcng/singularity)
["Introduction from San Diego Supercomputer Center"](https://www.youtube.com/watch?v=vEjLuX0ClN0)
1. What is a container?
A (software) container is an abstraction for a set of technologies that aim to solve the problem of how to get software to run reliably when move from one computing environment to another.

2. What is Singularity?
Singularity is a kind of container for HPC (High Performance Computing Clusters).

3. What can Singularity do for you?
It's a docker for HPC, that means it can do all the things that a container can do and you can let no trust users run untrusted containers. In the meanwhile, It supports HPC hardware and scientific applications.

## Container
<p align="center">
<a>
<img src="/img/singularity/shipping.png"
style="width:600px;">
Containers in digital world
</a>
</p>
Like what we ship goods with a container by ship, we put a huge variaty of goods in containers and ship them between warehouses, without container, it is less secured and will be a mess during the transport. As different servers or machines have different standards and different environment, we need to use container to make our applications run across different platform.

## Component of Singularity
1. Container Image: A file (or collection of files) saved on disk that stores everything you need to run a taget application or applications: code, runtime, system tools, libraries, etc.

2. Container Process: A container process is simply a standard(Linux) process running on top of the underlying host's operating system and kernel, but whose software environment is defined by the contents of the container image.

## Compare to Virtual Machines
Container-based applications have direct access to the host kernel and hardware and, thus, are able to achieve similar performance to native applications. In contrast, VM-based applications only have indirect access via the guest OS and hypervisor, which creates a significant performance overhead.

<p align="center">
<a href="https://www.weave.works/blog/a-practical-guide-to-choosing-between-docker-containers-and-vms">
<img src="/img/singularity/containers-vs-virtual-machines.jpg"
style="width:600px;">
Illustration of the structures of container and virtual machine. 
</a>
</p>

## Compare to Docker
1. HPC systems are shared resources and Docker is not designed for it.

2. Docker's security model is designed to support trusted users running trusted containers(e.g. Users can escalate to root). 

3. Docker is not designed to support tightly-coupled, highly distributed parallel applications(MPI).

## Most Common Singularity Use Cases
1. Building and running applications that require newer system libraries than those are available on host system.

2. Running commercial applications binairies that have specific OS requirements which are not met by host system.

3. Converting Docker containers to Singularity containers.


## The Singularity Workflow
1. **Build** your Singularity containers on a local system where you have root or sudo access; e.g., a personal computer where you have installed Singularity.

2. **Transfer** your Singularity containers to the HPC system where you wnat to run them.

3. **Run** your Singularity containers on that HPC system.

# Setup A singularity on HPC

It is recommanded to install the same version of Singularity used on the HPC system where you plan to run your containers. If you run on multiple HPC systems, then install the lowest version number you expect to use. It is better to use Ubuntu or Fedora-based local system. I chose to use Ubuntu 20.04 for this part.

Besides building a container there are also two interesting registry for Singularity.
1. [Sylabs.io HUB](https://cloud.sylabs.io/home) (commercialised)
2. [Singularity HUB](http://datasets.datalad.org/?dir=/shub) (oringinal)

They are like docker hub where you can build, share or download images.

## Useful documents
You may have a look at the detailed instructions to use [Singularity  Lab: Build A Container](https://github.com/singularityhub/singularityhub.github.io/wiki/Build-A-Container). 
There is also a very useful document [on Redhen about using Sigularity](https://sites.google.com/case.edu/techne-public-site/singularity).
There is also an introduction of using singularity on [Case Western Reserve HPC](https://sites.google.com/a/case.edu/hpcc/hpc-cluster/software/Software-Guide/s-t/singularity).
To install Singularity on your computer, have a look on [the official documents of Singularity container](https://sylabs.io/guides/3.3/user-guide/installation.html).

## Build an Openpose singularity container
1. Write a singularity definition file we name as openpose.def here. I followed steps introduced by Frankier and Zhiqi who are GSOC2020 students. You can have a look at their [github](https://github.com/frankier/openpose_containers). My definition file can be found on [My github](https://github.com/YunfeiZHAO/gsoc-redhen-2021/tree/main/singularity).
2. If you want to build Singularity container locally, you need to follow the [introduction here](https://singularity-tutorial.github.io/01-installation/). I chose the Sigularity version 2.5.2 which can aussi be used on my HPC server. If you want to build a container locally, you need to have enough space on your working space, it can easily take more than 1g of memory depends on your project.
3. To build a container, you need to have a root access and you can use this command to get into it.
    * **sudo -i**
    To run the build process, you need the command like this:
    * **sudo singularity build --sandbox openpose_container openpose.def**
4. After the building process, you will find a new folder is created named openpose_container. You can shell into the container as follows (-w means “writable):
    * **sudo singularity shell -w openpose_container**
5. To create the final portable unchangeable image (after training etc.):
    * **sudo singularity build openpose_container.simg openpose_container**
6. Finally, you can either upload the whole folder of openpose_container or openpose_container.simg on your HPC. It is recommended by using **rsync** command than use **scp**. Because you need to upload some very big files only once. If the connection is interrupted, you can continue the work by reusing the same command.
    * **sudo rsync --progress -a ./openpose_container/ server_domain_name:~/openpose_container/**
7. If you want to a container to have a shared folder with your host, you can use the following command.
    * **sudo singularity shell -w --bind ~/Desktop/container:/home  ubuntu_container**
    In this way, you can bind the folder ~/Desktop/container on your host to /home on your container.
8. To use a user in a container, but you do not in the sudoer group on HPC to change user. You can following these steps:
    * Create a home folder locally and mount the home folder on a container home directory when run it with sudo.
    * Add a user with the same user name on HPC and switch to this user. Install everything like Anaconda, etc.
    * Upload the container(If it is already on the HPC, you do not need to do this) and the home folder on HPC. 
    * Then, on HPC, you can run the container by binding the home directories like what you do locally, and you will find you are using the user in the container as the same name you have in HPC and the home directory is what you created locally.

9. Load some necessary modules on HPC:
    * **module load singularity**
    * **module load cuda**
    * **srun -p gpu \--gpus 1 \--mem 4000 \--cpus-per-gpu 2 \--pty bash # do -h to know more options**
    * **pestat -p gpu -w <hostname> # this will show memory usage, has to be run on another terminal**

10. Use GPU in singularity:
    * You can firstly have a look at this document from [Sylab.io](https://sylabs.io/guides/3.5/user-guide/gpu.html)
    * what I do is to use **singularity shell --nv --bind ./home:/home --bind /usr/local/cuda-11.2:/usr/local/cuda ubuntu_container**
    In this way you mount cuda directory and also a list of files in /usr/bin of the host to your conatainer:
    nvidia-cua-mps-control dnvidia-cuda-mps-server nvidia-debugdump nvidia-persistenced nvidia-smi
    * You need to add cuda path in your .bashrc and source it
    ``` CUDA
    export PATH=$PATH:/usr/local/cuda/bin
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
    ```