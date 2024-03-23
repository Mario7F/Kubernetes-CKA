## What is Kubernetes?

    - It is a container orchestration tool (docker, podman, etc)
    - Helps you manage containerized applications (100's or 1000's) in different environment (Pysical machine "server", virtual machine or cloud)

## What problems does Kubernetes solve? 

    - The rise of microservice technology (Trend from monolith to microservices - small independent services), Kubernetes provide a proper way of managing hundreds of containers.

##  What are the task of an orchestration tools?

    - To provide high availability (no down time), scalability (high performance) and disaster recovery (backup and restore)

## Kubernetes Basic Architecture

![images](https://github.com/Mario7F/RHEL9/assets/59115100/6231ff33-d0d7-4fbb-9a3b-87caf0f47b0b)

#### Master node - Kubernetes processes are running (api server, controller manager, scheduler and etcd)
#### Worker node (Kubelet)/node agent - these are where your applications (containers) are running
#### Api Server - Entry point to K8s (Kubernetes) cluster, the process where different kubernetes clients talk to, UI (Kubernetes dashboard), API ( if you are using some scripts and automation technology) and CLI (command line interface)
#### Controller Manager - Keeps track or an overview of whats happening in the cluster (if something needs to be repaired or if a container died and needs to be restarted)
#### Scheduler (sched) - Ensures pods placement, based on the work load, available server resources on each node
#### etcd - Kubernetes backing store, it holds the configuration data inside, status data of each node and container and the backkup and restore is made from the etcd snapshots

#### All of this is held together by virtual networking, it creates one unified machine

#### The worker nodes will be heavier due to the applications running inside of them

#### Master node is more important due to the fact that if you are unable to access the master you will not be able to access the cluster. As a best practice it is advised to at least have a backup of the master.

## Kubernetes Basic Concepts

#### Pods - are the smallest units as a Kubernetes user will configure and interact with. It is also a wrapper of the container. On each worker node there will be multiple pods, and inside of a pod there can be multiple containers usually per application you will have one pod so the only time you will need more than one container inside of pod is when you have a main application that need some helper container.

    - Usually one pod per application (database server, server, node.js, java application, etc)

#### Virtual network assign each pod its own ip address

    - Each pod is its own self-contain server with an ip address
    - They communicate with each other using the internal ip address

#### We do not create or configure containers inside the kubernetes cluster, we only work with the pods

    - If a container stops or dies inside of a pod, it will be automatically restarted inside of the pod.
    - Pods are frequently recreated, when this happens the pod get a new ip address

#### Service - alternative to (newly created ip address for new pods), they sit in front of each pod that talks to each other.

    - Permanent ip address to communicate between the pods
    - Its also a load balancer

#### Deployment - template for creating pods

