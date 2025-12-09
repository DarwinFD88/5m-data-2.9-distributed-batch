# Runbook: Setting up Dataproc on Google Cloud Free Tier  
  
**Author:** [Your Name/Organization]   
**Date:** 2025-12-08   
**Purpose:** Setup a 3-node Dataproc cluster within Free Tier limits (under 8 vCPUs) and configure correct distributed data access.  
  
---  
  
## 📋 Prerequisites  
* Google Cloud Project with Billing enabled (Free Trial is fine).  
* Google Cloud SDK (`gcloud`) installed or access to **Cloud Shell**.  
  
---  
  
## Phase 1: Environment & IAM Setup  
*Execute these commands in your local terminal or Google Cloud Shell.*  
  
### 1. Set Project Variables  
Replace the placeholders with your actual Project ID and Email.  
```bash  
export PROJECT_ID="your-project-id-here"  
export REGION="us-central1"  
export EMAIL="your-email@example.com"  
#gcloud config set project $PROJECT_ID  
```  

### 2. Enable Required APIs

Enable the necessary services for Dataproc, Compute Engine, and Storage.

  

```bash
gcloud services enable \  
    dataproc.googleapis.com \  
    compute.googleapis.com \  
    storage-component.googleapis.com  
```

### 3. Grant IAM Permissions

Ensure your account has permissions to manage clusters and storage objects.

```Bash  

gcloud projects add-iam-policy-binding $PROJECT_ID \  
    --member="user:$EMAIL" \  
    --role="roles/dataproc.editor"  
  
gcloud projects add-iam-policy-binding $PROJECT_ID \  
    --member="user:$EMAIL" \  
    --role="roles/storage.objectAdmin"  
  
```

## Phase 2: Create the Cluster

This configuration creates a 3-node cluster using 6 vCPUs total, fitting safely within the 8 vCPU Free Trial limit.


```Bash

gcloud dataproc clusters create $CLUSTER_NAME \
    --region=$REGION \
    --zone=$ZONE \
    --master-machine-type=n1-standard-2 \
    --master-boot-disk-size=32GB \
    --num-workers=3 \
    --worker-machine-type=n1-standard-2 \
    --worker-boot-disk-size=32GB \
    --image-version=2.1-ubuntu20 \
    --enable-component-gateway \
    --optional-components=JUPYTER,ZEPPELIN
  

Wait approximately 2–4 minutes for the cluster to reach the RUNNING state.
```
## Phase 4: Running the Job (Jupyter)

1. Navigate to Dataproc > Clusters > my-cluster.
    
2. Click the Web Interfaces tab.
    
3. Click JupyterLab to open the interface.
    
4. Upload jupyter notebook

5. Select the PySpark kernel.
    


## Phase 5: Clean Up

To avoid unnecessary billing charges, delete the cluster when finished.

```Bash
gcloud dataproc clusters delete my-cluster --region=$REGION --quiet  
```