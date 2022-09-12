# Template materials in Octave

Example repository to create an environment with course materials in Octave.

The [Octave kernel](https://github.com/Calysto/octave_kernel) is provided by Calysto.

## Try it on Binder

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/plasmabio/template-octave/master?urlpath=%2Flab/)


## Check Octave is properly installed

In JupyterLab, open a terminal and type :

```bash
octave --version
```

You should have an output similar to:

```bash
$ octave --version
octave: X11 DISPLAY environment variable not set
octave: disabling GUI features
GNU Octave, version 7.1.0
Copyright (C) 1993-2022 The Octave Project Developers.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.

Octave was configured for "x86_64-conda-linux-gnu".

Additional information about Octave is available at https://www.octave.org.

Please contribute if you find this software useful.
For more information, visit https://www.octave.org/get-involved.html

Read https://www.octave.org/bugs.html to learn how to submit bug reports.
```

Warnings:

```
octave: X11 DISPLAY environment variable not set
octave: disabling GUI features
```
do not prevent graphics to be dislayed in Jupyter notebook.

Also do check octave kernel is available:

```bash
$ jupyter kernelspec list
Available kernels:
  octave     /srv/conda/envs/notebook/share/jupyter/kernels/octave
  python3    /srv/conda/envs/notebook/share/jupyter/kernels/python3
```

## Install Octave packages

In a terminal, with `octave` loaded or in notebook with the Octave kernel, run:
```
pkg install -local -forge io statistics struct optim
```
This will take a couple of minutes. Some warning message might be printed.

Then list available packages:
```
pkg list
```

And test the `optim` package:
```
pkg test optim
```


## Structure of the repo

This repository is based on the [binder-examples/conda](https://github.com/binder-examples/conda) example.

[`repo2docker`](https://repo2docker.readthedocs.io) is the underlying tool that is used to build an environment from a repository.

`repo2docker` can be configured with several types of files. In the case of this repo:

- `binder/environment.yml`: specify dependencies that will be installed using `conda`
- `binder/apt.txt`: specify regular Ubuntu packages that will be installed using `apt`

Once created, the environment can be reused without building it again.

For more information, see the [extensive rep2docker documentation](https://repo2docker.readthedocs.io).

## Materials

Materials can be added anywhere to this repository, either at the top level or in subdirectory.

When building the environment, the materials (and any other file) will be copied to the Docker image.

In this example, there is already a test notebook available under `example-notebook-octave.ipynb`.
