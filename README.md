# ATC Round 1 - Kubernetes

## Step-01: Cluster creation
- Clone the repository and go to the ATC_round1 directory
- Execute the script with help option to see required arguments

```
  python3 create_cluster.py --help
  usage: create_cluster.py [-h] --rgName RGNAME --clusterName CLUSTERNAME
                         --nodeCount NODECOUNT

  Deploy Kubernetes Cluster on Azure

  optional arguments:
    -h, --help            show this help message and exit
    --rgName RGNAME, -r RGNAME
                          Enter Resource Group
    --clusterName CLUSTERNAME, -c CLUSTERNAME
                          Enter Cluster Name
    --nodeCount NODECOUNT, -n NODECOUNT
                          Enter Node Count
```

- Execute python with above arguments to mention the resource group, cluster name and node count to be deployed

```
  python3 create_cluster.py -r kubecluster -c cluster1 -n 1
```

- The script will take around 5-10 minutes to execute and once complete, will create a cluster with given number of nodes in the mentioned resource group and will set it to default

## Step-02: Create deployment and service
- Run kubectl apply command on the templates directory to create deployment and a service

```
  kubectl apply -f templates/
```

- This will create a nodejs service which scales upto 4 pods based on the CPU utilization. If CPU utilization is more than 5%, a new pod is created automatically

- This will create a Load Balancer service which exposes port 8081

- This will create a secret with environment variables called api_user and api_token in the POD 

- This will create an Ingress controller to provide an SSL Termination

- This will create a secret with SSL generated keys and added them to the pod at /tmp/ directory
