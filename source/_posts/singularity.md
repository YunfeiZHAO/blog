---
title: GSOC week0 - Singularity
date: 2021-05-30 12:13:53
category: GSOC 2021 Redhen
tags: [HPC]
excerpt: Community bonding period with Redhen during Google Summer of Code 2021. An introduction to the community, my project and Singularity on HPC. (May 17, 2021 - May 30, 2021)
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

