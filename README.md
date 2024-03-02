# SampleMERNwithMicroservices
Step 1: Clone the Repository
Open a terminal or command prompt.

Use the git clone command to clone the MERN application repository from GitHub:
bash
Copy code
git clone https://github.com/UnpredictablePrashant/SampleMERNwithMicroservices.git

Navigate to the cloned repository:
bash
Copy code
cd SampleMERNwithMicroservices


Step 2: Set Up Azure Environment
Log in to your Azure account using the Azure CLI:
bash
Copy code
az login
Set the subscription you want to use for the AKS cluster:
bash
Copy code
az account set --subscription <subscription_id>
Create a resource group for your AKS cluster:
bash
Copy code
az group create --name <resource_group_name> --location <location>
Create an AKS cluster:
bash
Copy code
az aks create --resource-group <resource_group_name> --name <cluster_name> --node-count <node_count> --node-vm-size <vm_size> --enable-addons monitoring --generate-ssh-keys


Step 3: Deploy MongoDB
Deploy MongoDB on your AKS cluster. You can use Helm charts or YAML manifests for deployment.


Step 4: Build and Deploy Backend
Build the backend Docker image:
bash
Copy code
cd backend
docker build -t <backend_image_name> .
Push the backend image to a container registry (e.g., Azure Container Registry).

Deploy the backend application to AKS using Kubernetes YAML manifests or Helm charts.

Step 5: Build and Deploy Frontend
Build the frontend Docker image:
bash
Copy code
cd ../frontend
docker build -t <frontend_image_name> .
Push the frontend image to a container registry.

Deploy the frontend application to AKS using Kubernetes YAML manifests or Helm charts.

Step 6: Access Your Application
Get the external IP address of the AKS cluster:
bash
Copy code
kubectl get services
Access your MERN application using the external IP address and appropriate ports.


Step 7: Clean Up (Optional)
If you no longer need the resources, you can delete the AKS cluster and associated resources:

bash
Copy code
az aks delete --name <cluster_name> --resource-group <resource_group_name>
