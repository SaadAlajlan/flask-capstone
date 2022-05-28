# flask-capstone
[![CircleCI](https://circleci.com/gh/SaadAlajlan/flask-capstone/tree/main.svg?style=svg)](https://circleci.com/gh/SaadAlajlan/flask-capstone/tree/main)

### Introduction

This project "operationalize" a sample python/[flask](https://flask.palletsprojects.com/)
demo app ["hello"](./hello_app/hello.py), using [CircleCI](https://www.circleci.com) and
 a [Kubernetes](https://kubernetes.io/)(K8S) cluster deployed in [AWS EKS](https://aws.amazon.com/eks/)(Amazon Elastic Kubernetes Services):
 * In a [CircleCI](https://www.circleci.com) pipeline, we lint the project's code, build
 a Docker image and deploy it to a public
Docker Registry: [Docker Hub](https://hub.docker.com/repository/docker/saadaj/hello-app)
* Then in an [AWS EKS](https://aws.amazon.com/eks/) cluster, we run the application

All the project's tasks are included in a [Makefile](Makefile), which uses several shell scripts stored in the
[bin](bin) directory.

The CirclCI pipeline([config.yml](.circleci/config.yml)) will execute the following steps automatically:

* `make setup`
* `make install`
* `make lint`
* Build and publish the container image
you can:
* Deploy a Kubernetes cluster:  `make eks-create-cluster`
* Deploy the application:  `make k8s-deployment`
* Update the app in the cluster, using a rolling-update strategy:  `make rolling-update`
* Delete the cluster:  `make eks-delete-cluster`

To verify that the app is working, write your deployment's IP into your browser using port 80, like
`http://localhost:80` or `http://LOAD_BALANCER_IP:80` 
