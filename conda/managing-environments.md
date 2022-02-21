---
layout: default
title: Managing Environments
nav_order: 1
parent: Conda
---

# Managing Environments
{: .no_toc }

1. TOC
{:toc}

## Creating Environments

### Empty Environment

1. Create the environment:

    ```bash
    conda create -n demo_env
    ```

2. Activate the environment: (don't forget this!)

    ```bash
    conda activate demo_env
    ```

3. Install packages:

    ```bash
    conda install ipykernel numpy pandas
    ```

### Environment with Required Packages
Do it all in one line:

```bash
conda create -n demo_env ipykernel numpy pandas
```

## Adding Environments as Jupyter Kernels
Ensure your environment has `ipykernel` installed:

```bash
conda activate demo_env
conda install ipykernel
```

Then, add the kernel to Jupyter:

```bash
ipython kernel install --user --name=demo_env
```