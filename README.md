# Deploy simple app on OpenShift

This repo contains all Kubernetes resources necessary to deploy a Docker image from Docker Hub to OpenShift.

Docker image: https://hub.docker.com/r/pmgysel/spring-boot-app

## Option 1: Use OpenShift Web Console (GUI)

* Login to [OpenShift](https://manage.openshift.com/sign_in)
* In "Developer" view, choose your preferred "Project"
* Choose "+Add" -> "YAML"
* Copy-paste the "deployment.yaml" file from this repo, click "Create"
* Repeat with "service.yaml" and "route.yaml"
* In "Administrator" view, choose "Networking" -> "Routes"
* Click on "Location" link -> this is a direct route to your running Docker container
* Add "/api/ping/" to link -> Now you should see an answer from your app running on OpenShift

## Option 2: Use CLI (oc command)

Login to OpenShift (info under "?" -> "Command Line Tools" -> "Copy Login Command")
```shell
$ oc login --token=[...] --server=[...]
```

Choose your preferred project:
```shell
$ oc project <YOUR_OS_PROJECT>
```

Upload all Kubernetes resources:
```shell
$ oc apply -f deployment.yaml
$ oc apply -f service.yaml
$ oc apply -f route.yaml
```
