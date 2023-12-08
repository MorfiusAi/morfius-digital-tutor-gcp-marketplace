# morfius-digital-tutor-gcp-marketplace

# Overview

The Morfius Digital Tutor app enhances the educational experience by adapting approved curriculum into 
engaging and accessible resources and knowledge bases. It offers unique features like video transcription and translation,
enabling teachers to cater to diverse student needs, including English Language Learners and those with visual or auditory impairments. 
Additionally, Digital Tutor provides powerful analytics for teachers and administrators to track student performance and engagement, 
ensuring a more personalized and efficient learning process. 
This personalized AI generative app is optimized for fast development, training, and low cost runtime, offering a secure environment for educational data.

# Installation

## Quick install with Google Cloud Marketplace

Get up and running with a few clicks! Install this Morfius Digital Tutor app to a
Google Kubernetes Engine cluster using Google Cloud Marketplace. Follow the on-screen
instructions:

## Command line instructions

Follow these instructions to install Morfius Digital Tutor from the command line.

### Prerequisites

#### Set up command-line tools

You'll need the following tools in your development environment. If you are
using Cloud Shell, `gcloud`, `kubectl`, Docker, and Git are installed in your
environment by default.

-   [gcloud](https://cloud.google.com/sdk/gcloud/)
-   [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)
-   [docker](https://docs.docker.com/install/)
-   [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

Configure `gcloud` as a Docker credential helper:

```shell
gcloud auth configure-docker
```

#### Create a Google Kubernetes Engine (GKE) cluster

Create a new cluster from the command line:

```shell
export CLUSTER=wordpress-cluster
export ZONE=us-west1-a

gcloud container clusters create "$CLUSTER" --zone "$ZONE"
```

Configure `kubectl` to connect to the new cluster:

```shell
gcloud container clusters get-credentials "$CLUSTER" --zone "$ZONE"
```

#### Clone this repo

Clone this repo:

```shell
git clone --recursive https://github.com/MorfiusAi/morfius-digital-tutor-gcp-marketplace.git
```

#### Install the Application resource definition

An Application resource is a collection of individual Kubernetes components,
such as Services, Deployments, and so on, that you can manage as a group.

To set up your cluster to understand Application resources, run the following
command:

```shell
kubectl apply -f "https://raw.githubusercontent.com/GoogleCloudPlatform/marketplace-k8s-app-tools/master/crd/app-crd.yaml"
```

You need to run this command once.

The Application resource is defined by the
[Kubernetes SIG-apps](https://github.com/kubernetes/community/tree/master/sig-apps)
community. The source code can be found on
[github.com/kubernetes-sigs/application](https://github.com/kubernetes-sigs/application).

#### Install license key

Visit the application's config page in Google Cloud Console, and download the license key
from the "Deploy via command line" tab. Apply it in the target namespace.


### Install the application

Set environment variables (modify if necessary):
```
export name=morfius-digital-tutor
export namespace=default

# Use the name of the secret created for the license key
export reportingSecret=<license-key-secret-name>
```

Expand manifest template:
```
cat manifest/* | envsubst > expanded.yaml
```

Run kubectl:
```
kubectl apply -f expanded.yaml
```
