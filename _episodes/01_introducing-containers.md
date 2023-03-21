---
title: "1. Introducing Containers"
teaching: 5
exercises: 0
questions:
- "What are containers, and why might they be useful to me?"
objectives:
- "Show how software depending on other software leads to configuration management problems."
- "Identify the problems that software installation can pose for research."
- "Explain the advantages of containerization."
- "Explain how using containers can solve software configuration problems"
keypoints:
- "Almost all software depends on other software components to function, but these components have independent evolutionary paths."
- "Small environments that contain only the software that is needed for a given task are easier to replicate and maintain."
- "Critical systems that cannot be upgraded, due to cost, difficulty, etc. need to be reproduced on newer systems in a maintainable and self-documented way."
- "Virtualization allows multiple environments to run on a single computer."
- "Containerization improves upon the virtualization of whole computers by allowing efficient management of the host computer's memory and storage resources."
- "Containers are built from 'recipes' that define the required set of software components and the instructions necessary to build/install them within a container image."
- "Docker is just one software platform that can create containers and the resources they use."
---

> ## Docker for Research
>
> Introductory video by the Australian Research Data Commons
>
> [How can software containers help your research?](https://www.youtube.com/watch?v=HelrQnm3v4g)
>
> Australian Research Data Commons, 2021. *How can software containers help your research?*. [video] Available at: https://www.youtube.com/watch?v=HelrQnm3v4g DOI: http://doi.org/10.5281/zenodo.5091260
{: .callout}


## Scientific Software Challenges

> ## What's Your Experience?
>
> Bring to mind challenges you've fased using software for your research.
{: .challenge}

The following are common, and you may relate:

- Incompatible OS.
- Many dependencies of dependencies ...
- Unexpected behavior depending on versions and OS.
- It works on your computer but not on someone else's or a cluster.
- Reproducing results from a lab member who graduated.

The problem: software can be fragile and break with small changes.

> ## Software and Science
>
> What does this mean for your research and science at-large?
{: .challenge}

Science depends on software, so there are problems with fragile software:
- A tool for published results is not available or installable.
- You can't reproduce your own results.
- Others can't build on your work because they need to start from scratch.

Containers enable the consistent packaging of software dependencies and resource access, such as files and networks.

## What is a Container? What is Docker?
The three fundamental elements in Docker are the Dockerfile, the image, and the container:

**Docker** is a tool for creating and running Docker containers from Docker images, which can be made interactively or using a Dockerfile.

A **container** is a running process on a computer instantiated from an image. It's like a shipping container because it encapsulates its contents in a standardized, portable, and efficient way.  

An **image** is an immutable compiled binary executable snapshot of software and all dependencies, down to the OS. It can be used to make one or many identical running containers.

A **Dockerfile** is a script that, when executed, tells Docker how to build image.


> ## Virtualization
>
> Containers are an example **virtualization** -- having a
> second "virtual" computer running and accessible from a main or **host**
> computer. Another example of virtualization are **virtual machines** or
> VMs. A virtual machine typically contains a copy of an operating system in
> addition to its own filesystem and has to get booted up in the same way
> a computer would.
> A container is considered a lightweight version of a virtual machine;
> underneath, the container is (usually) using the Linux kernel and simply has some
> flavor of Linux + the filesystem inside.
{: .callout}

## Addressing Research Problems with Containers

Think back to some of the challenges we described at the beginning. The many layers
of scientific software installations make it hard to install and re-install
scientific software -- which ultimately, hinders reliability and reproducibility.

But now, think about what a container is -- a self-contained, complete, separate
computer filesystem. What advantages are there if you put your scientific software
tools into containers?

This solves several of our problems:

- documentation -- there is a clear record of what software and software dependencies were used, from bottom to top.
- portability -- the container can be used on any computer that has Docker installed -- it doesn't matter whether the computer is Mac, Windows or Linux-based.
- reproducibility -- you can use the exact same software and environment on your computer and on other resources (like a large-scale computing cluster).
- configurability -- containers can be sized to take advantage of more resources (memory, CPU, etc.) on large systems (clusters) or less, depending on the circumstances.

The rest of this workshop will show you how to download and run containers from pre-existing
container images on your own computer, and how to create and share your own container images.

## Use cases for containers

Now that we have discussed a little bit about containers -- what they do and the
issues they attempt to address -- you may be able to think of a few potential use
cases in your area of work. Some examples of common use cases for containers in
a research context include:

- Using containers solely on your own computer to use a specific software tool
  or to test out a tool (possibly to avoid a difficult and complex installation
  process, to save your time or to avoid dependency hell).
- Creating a `Dockerfile` that generates a container image with software that you
  specify installed, then sharing a container image generated using this Dockerfile with
  your collaborators for use on their computers or a remote computing resource
  (e.g. cloud-based or HPC system).
- Archiving the container images so you can repeat analysis/modelling using the
  same software and configuration in the future -- capturing your workflow.

{% include links.md %}

{% comment %}
<!--  LocalWords:  keypoints links.md endcomment
 -->
{% endcomment %}
