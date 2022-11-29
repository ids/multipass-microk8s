Multipass MicroK8s
==================

Some simple BASH scripts to create multi-node MicroK8s using Multipass with the VirtualBox driver.  The VirtualBox driver is used because HyperKit doesn't support "pause/suspend" at the present time, and pause is very useful when testing K8s over time.

Requirements:
-------------

- Install [Multipass](https://multipass.run/install)
- Install [VirtualBox 7](https://www.virtualbox.org/)
- Install `kubectl` (brew install kubectl on macOS)

You will also need the macOS XCode command line tools installed.

Setup:
------

Setup the Kubernetes Host-Only Network in VirtualBox:

```
$ bash create-network
```

Configuration for the K8s clusters is stored in the `env` file.  Adjust the environment variables to suit your cluster requirements.

```
CB_MASTER_NODES=1
CB_WORKER_NODES=2

CB_NETWORK=KubernetesNetwork 

CB_MASTER_NAME=k8s-master
CB_WORKER_NAME=k8s-worker

CB_MASTER_CPU=4
CB_MASTER_DISK=30G
CB_MASTER_RAM=4G

CB_WORKER_CPU=4
CB_WORKER_DISK=50G
CB_WORKER_RAM=8G

```

Building MicroK8s Clusters
--------------------------

Create the VMs for the cluster:

```
$ bash create-vms
```

And then build the cluster:

```
$ bash build-cluster
```


Managing MicroK8s Cluster VMs
-----------------------------

```
$ bash cluster start | stop | pause
```

Cleaning Up
-----------

```
$ bash delete-vms
```


