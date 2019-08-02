# Workshop

This is the outline for the GopherCon 2019 workshop [Go & Kubernetes Sitting In A Tree](https://www.gophercon.com/agenda/session/70232).

# Tools

- kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/
- kubefwd: https://github.com/txn2/kubefwd/releases
- Helm: https://github.com/helm/helm#Install
- Telepresence: https://www.telepresence.io/reference/install
- Garden: https://docs.garden.io/basics/installation
- Skaffold: https://skaffold.dev/docs/getting-started/#installing-skaffold
- Tilt: https://docs.tilt.dev/install.html
- stern: https://github.com/wercker/stern#Installation
- Squash: https://github.com/solo-io/squash/releases

# Index

### Introduction
- Overview of the Go part.
- Overview of the Kubernetes tooling part.
- Example app overview.

### First steps & interacting with pods in a cluster:
- Creating an optimized Dockerfile for Go
- Overview of a Kubernetes manifest
- Deploying to cluster old school-style with kubectl&docker.
- Using kubefwd
- Using Telepresence

### Advanced techniques & the optimal development workflow:
- Skaffold and Tilt
- Using _Garden_ for complex systems. Dependencies, tests (unit & e2e), in-cluster building.
- REST vs. gRPC

### Debugging:
- Basics of _kubectl debugging._
- Distributed debuggers with _Squash._

***

# Materials

## Kubernetes Tooling

The material presented originates from this talk
- Link to the talk https://www.youtube.com/watch?v=dIs8FwJzVI8
- Link to slides https://garden.slides.com/ellenkorbes/k8sdevtools?token=t3egVfZS#/

## Example app overview

It's structured in such and such a way and this is what it does.

Link: https://github.com/campoy/links

## Creating an optimized Dockerfile for Go

- Use vendoring
- Use multi-stage builds
- Example:

## Overview of a Kubernetes manifest

Include example manifest and explain it.

## Deploying to cluster with kubectl&docker

The main workflow consists of:

- Make changes to your code.
- Build a new image: `docker build -t user/repo:1.0 .`
- Tag it: `docker tag image registry.com/user/repo:1.0`
- Push the image to a registry: `docker push registry.com/user/repo:1.0`
- Update your cluster: `kubectl apply -f obj.yaml`

To do that, you need to have set up in advance:
- docker login (for the registry)
- Dockerfile
- Kubernetes manifest

## Using kubefwd

- What's kubefwd?
- kubefwd in action: `sudo kubefwd svc -n namespace`

## Using Telepresence

- What's kubefwd?
- kubefwd in action.

## Skaffold

What it does:
- Build & deploy
- Hot reload

What you need:
- Simple configs
- Kubernetes manifests

Best fit for:
- Quickly setting up simple projects

## Tilt

What it does:
- Everything Skaffold does
- Dashboard
- Log streaming

What you need:
- Same as Skaffold

Best fit for:
- Same as Skaffold

## Garden

What it does:
- Build & deploy
- Stack graph/dependencies
- Tests
- In-cluster building
- Hot reload
- Dashboard
- Log streaming

What you need:
- Describe your system via config files

Best fit for:
- Complex projects with lots of moving parts

### kubectl debugging

Basic commands:

- `kubectl apply -f obj.yaml`
- `kubectl delete -f kuard-pod.yaml`
- `kubectl exec -it pod -- bash`
- `kubectl cp <pod-name>:/path/to/remote/file /path/to/local/file`
- `kubectl delete <resource-name> <obj-name>`
- `kubectl logs -f <pod>`
- `kubectl get pods/ns`
- `kubectl describe pods <pod>`
- `kubectl port-forward <pod> 8080:8080`
- `kubectl expose deployments <name> --port=2368`
- `kubectl run <name> --image=registry.com/user/repo:1.0`

Link to cheat sheet
Link to 'debugging with kubectl doc'

### Squash

- Link to dlv article
- Attach a debugger to a running container
- Multiple containers simultaneously
