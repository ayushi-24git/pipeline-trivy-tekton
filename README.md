
<h1>
Pipeline-trivy-tekton

</h1>
This repository demonstrates Trivy, a vulnerability management tool for images and containers. It uses Tekton pipeline under the hood.  


This repository contains a single task for scanning an image or a repository through Trivy. First, user is asked to choose between image and repo, whichever is to be scanned. Then a suitable image/repo link is given as a parameter. Further working of Trivy can be understood [here](https://rastogee-ayushi.medium.com/trivy-keep-your-artifacts-vulnerability-free-6dce292134e5). 

## Setting up cluster
Set up a cluster using minikube by doing a minikube start.

## Setting up Tekton
Install tekton with the following command after setting up the cluster

kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml

This will install all the necessary Tekton components to get started.

## Applying the Tasks and Pipeline yamls
Apply all the mentioned tasks in the repositorry above. Example format:

kubectl apply -f https://raw.githubusercontent.com/ayushi-24git/pipeline-trivy-tekton/main/tasks/scan.yaml

Apply the pipeline yamls as:

kubectl apply -f https://raw.githubusercontent.com/ayushi-24git/pipeline-trivy-tekton/scan-pipeline.yaml

kubectl apply -f https://raw.githubusercontent.com/ayushi-24git/pipeline-trivy-tekton/scan-pipelinerun.yaml

Now, start the pipeline by: `tkn pipeline start scan-pipeline`


Check logs
Now, the pipeline has successfully started. You can check the logs using the following command:

`tkn pipelinerun logs <name-of-the-pipelinerun>`.  

You can see the table of all vulnerabilities (if any) detected by Trivy.

  
