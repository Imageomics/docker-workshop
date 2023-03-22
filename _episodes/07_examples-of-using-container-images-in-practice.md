---
title: "7. Examples of Using Container Images in Practice"
teaching: 10
exercises: 0
questions:
- "How can I use Docker for my own work?"
objectives:
- "Use existing container images and Docker in a research project."
keypoints:
- "There are many ways you might use Docker and existing container images in your research project."
---

Now that we have learned the basics of working with Docker container images and containers,
let's apply what we learned to an example workflow component.

You may choose one or more of the following examples to practice using containers.

## Data Commons Access

In this example, you can use the [Dataverse Access](https://github.com/Imageomics/dataverse-access) command line tool to interface with the Ohio State University instance of the [Dataverse](https://dataverse.org/) called the [Data Commons](https://datacommons.tdai.osu.edu/).

To get the tool, run:
~~~
$ docker image pull ghcr.io/imageomics/dataverse-access
~~~
{: .language-bash}

Since this is a relatively long name, we might save time with it by renaming using the `tag` command.
~~~
$ docker tag ghcr.io/imageomics/dataverse-access dva-image
~~~
{: .language-bash}

Now, let's see what running it does:
~~~
$ docker container run dva-image 
~~~
{: .language-bash}
~~~
Usage: dva [OPTIONS] COMMAND [ARGS]...

Options:
  --help  Show this message and exit.

Commands:
  download  Download files within dataset DOI to DEST folder.
  ls        List files within a Dataverse dataset DOI.
  setup     Create config file to store a Dataverse URL and token for use...
  upload    Upload SRC files to a pre-existing dataset(DOI).
~~~
{: .output}

It looks like we can use this tool to `ls` data within a DOI. Let's try an example.
~~~
$ docker run dva-image dva ls doi:10.5072/FK2/B7LCCX --url https://datacommons.tdai.osu.edu/
~~~

We can use this tool to download data with a dedicated DOI by mounting a local volume to our current directory.
~~~
$ docker container run -v $(pwd)/data:/data -it dva-image dva download doi:10.5072/FK2/B7LCCX /data --url https://datacommons.tdai.osu.edu/
~~~
{: .language-bash}
Note: using Git Bash on Windows will require the addition of an extra `/` before paths and prefixing `winpty` before the command.
~~~
$ winpty docker container run -v /$(pwd)/data://data -it dva-image dva download doi:10.5072/FK2/B7LCCX //data --url https://datacommons.tdai.osu.edu/
~~~
{: .language-bash}


## Jekyll Website Example

In this [Jekyll Website example](../e02-jekyll-lesson-example), you can practice
rendering this lesson website on your computer using the Jekyll static website generator in a Docker container.
Rendering the website in a container avoids a complicated software installation; instead of installing Jekyll and all the other tools needed to create the final website, all the work can be done in the container.
Additionally, when you no longer need to render the website, you can easily and cleanly remove the software from your computer.

## GitHub Actions Example

In this [GitHub Actions example](../e01-github-actions), you can learn more about
continuous integration in the cloud and how you can use container images with GitHub to
automate repetitive tasks like testing code or deploying websites.

{% comment %}
<!--- Placeholder for
## Geospatial Example

Ask @mkuzak to make a PR to add extra for <https://github.com/escience-academy/docker-gdal-demo>

-->
{% endcomment %}

## Using Containers on an HPC Cluster

It is possible to run containers on shared computing systems run by a university or national
computing center. As a researcher, you can build container images and test containers on your own
computer and then run your full-scale computing work on a shared computing
system like a high performance cluster or high throughput grid.

The catch? Most university and national computing centers do not support *running*
containers with Docker commands, and instead use a similar tool called Singularity or
Shifter. However, both of these programs can be used to run containers based on Docker container images,
so often people create their container image as a Docker container image, so they can
run it using either of Docker or Singularity.

There isn't yet a working example of how to use Docker container images on a shared
computing system, partially because each system is slightly different, but the
following resources show what it can look like:

- [Introduction to Singularity](https://carpentries-incubator.github.io/singularity-introduction/): See the episode titled "Running MPI parallel jobs using Singularity containers"
- [Container Workflows at Pawsey](https://pawseysc.github.io/container-workflows/): See the episode titled "Run containers on HPC with Shifter (and Singularity)"

## Seeking Examples

Do you have another example of using Docker in a workflow related to your field?  Please [open a lesson issue] or [submit a pull request] to add it to this episode and the extras section of the lesson.


{% include links.md %}

[submit a pull request]: https://github.com/carpentries-incubator/docker-introduction/pulls
