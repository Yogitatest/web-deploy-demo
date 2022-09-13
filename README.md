# webapp-demo

## About:
The documentation help to understand building Webapp package with github action, creating docker iamge and deploying with kubernetes and helm charts.

## Requirements:

1. Github action workflow for build and creating docker iamge
2. Docker repository to push docker image
3. helm	-3.0.2
4. Kubernetes	-1.17


## Folder Structure:

-github/workflows
-src/
-pom.xml
-dockerfile
-helm-charts
  -Charts.yaml
  -Values.yaml
  -templates
    -deployments.yaml
    -service.yaml

* Building App - .github/workflows contains maven.yaml workflow to build and create docker iamge.
* Deploying App -The root directory contains helm chart for application deployment on Kubernetes cluster.

### What is Helm Chart:

- Helm is a package manager for Kubernetes that allows developers to easily configure and deploy applications on Kubernetes clusters.
- Helm uses a packaging format called charts.
- A chart is a collection of files that describe the Kubernetes resources
	
## File Usage:

Chart.yaml: contains metadata about the chart itself: its name, the chart version, a description, and similar details.

values.yaml: contains configuration settings for the chart. The defined values will be used by deployment template.

deployment.yaml: For deploying our application on Kubernetes cluster first step is to create POD that host the application container. But since pods are ephemeral by nature,
we need to create a higher controller that takes care of our pod (restart if it crashes, move it around nodes, etc.). For that reason, we’ll use a Deployment. Deployments also help to deploy more than one replica for our application.
With the help of values. yaml, deployment template can get parameterized for different environment.


## How To Run:

** .Set up infrastructure
    -Method1: install helm and kubernetse on VM.Clone the code and run command below
        * Command: helm install webapp ./helm-charts --namespace=default
    -Method2: create kubernetes cluster on cloud platform and deploy helm chart on cluster.

