# flask-capstone
[![CircleCI](https://circleci.com/gh/SaadAlajlan/flask-capstone/tree/main.svg?style=svg)](https://circleci.com/gh/SaadAlajlan/flask-capstone/tree/main)


https://github.com/SaadAlajlan/flask-capstone

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

### lint
![Screenshot 2022-05-28 191655](https://user-images.githubusercontent.com/38673587/170834595-b5e3fcec-e344-4711-ae88-d6101ccdf39f.jpg)
* success
![Screenshot 2022-05-28 191740](https://user-images.githubusercontent.com/38673587/170834598-72e13da9-c76c-42bb-9a6a-2355ad09a457.jpg)
* success workflow
![Screenshot 2022-05-31 005807](https://user-images.githubusercontent.com/38673587/171063020-9417829e-23f9-4c14-924c-b79740e7deb3.jpg)
* EC2
![Screenshot 2022-05-31 010323](https://user-images.githubusercontent.com/38673587/171063297-e5048326-9e4a-4236-8d04-a3b37423ec80.jpg)


#### First dyployment.
http://a92b0843bc5e54a4ba5278c60fb6d668-682203505.us-west-2.elb.amazonaws.com/

![Screenshot 2022-05-28 183705](https://user-images.githubusercontent.com/38673587/170834404-b1ad3df5-1f4c-4e02-b599-fb83bf235bbc.jpg)
#### second dyployment.
using 'make rolling-update'
![Screenshot 2022-05-28 183743](https://user-images.githubusercontent.com/38673587/170834512-c9206fb1-2682-40c7-8649-40e874e2512e.jpg)
![Screenshot 2022-05-28 183902](https://user-images.githubusercontent.com/38673587/170834572-5bc8428a-ce3c-4c61-9112-75fc01a7a396.jpg)

