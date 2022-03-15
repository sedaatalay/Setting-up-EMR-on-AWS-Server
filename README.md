# Setting up EMR on AWS Server
<p> <br/ >

## 1-Setup
## 2-Cluster Creation

<p> <br/ >
  
### 1-Setup
#### A- Create ec2 key pair
##### -Select the item Create Key Pair.
##### -Give your key pair a name and choose:
“RSA”
“.pem” 
<img width="818" alt="Ekran Resmi 2022-03-15 20 43 13" src="https://user-images.githubusercontent.com/91700155/158467944-9401b138-b1d9-429b-bd7a-6aa365d06c99.png">


#### B- Create S3 bucket
##### -Open the AWS console and navigate to the S3 service.
##### -Select Create Bucket.
  
##### S3 General Configuration
<img width="1025" alt="Ekran Resmi 2022-03-15 20 50 45" src="https://user-images.githubusercontent.com/91700155/158467989-ee4391fa-ab87-4519-b0ce-b2ace256c166.png">
##### To open Public Access
<img width="1012" alt="Ekran Resmi 2022-03-15 20 51 42" src="https://user-images.githubusercontent.com/91700155/158468061-38667f8f-22b4-4634-8701-e07c63837ca9.png">
##### We can create folder to keep i.e. logs, data..
<img width="1371" alt="Ekran Resmi 2022-03-15 20 56 39" src="https://user-images.githubusercontent.com/91700155/158468102-a6a83915-9e1e-4378-bad1-99a911790608.png">
<img width="666" alt="Ekran Resmi 2022-03-15 20 57 50" src="https://user-images.githubusercontent.com/91700155/158468144-bd6d2d22-6150-4d20-a864-106829cf3bdd.png">
##### The folder has been created.
<img width="1138" alt="Ekran Resmi 2022-03-15 21 00 05" src="https://user-images.githubusercontent.com/91700155/158469652-0aab4c71-3b7f-4c84-a044-1900a5c87084.png">


### 2- Cluster Creation
#### A- Launch EMR Cluster
##### -Open the AWS console and navigate to the EMR service.
##### -Select Create Cluster.
<img width="904" alt="Ekran Resmi 2022-03-15 21 06 28" src="https://user-images.githubusercontent.com/91700155/158468249-5b0762e2-73a2-4f7e-a2b8-cf06255b68d1.png">
  
##### Select Go to advanced options.
<img width="872" alt="Ekran Resmi 2022-03-15 21 07 02" src="https://user-images.githubusercontent.com/91700155/158468312-bdaf6ec8-cdd2-472f-82c4-550e8fef9f61.png">

##### Step-1
###### For the section titled Software Configuration select the in the picture following options.
<img width="886" alt="Ekran Resmi 2022-03-15 21 08 43" src="https://user-images.githubusercontent.com/91700155/158468331-d67088ee-2541-4156-8bf4-6f685f491ed4.png">

##### Step-2
###### For the Hardware Configuration select the following options. 
Choose the VPC configuration with a Single Public Subnet which is "yousefVPC"
<img width="927" alt="Ekran Resmi 2022-03-15 21 11 20" src="https://user-images.githubusercontent.com/91700155/158468361-0ca4a78f-a600-4cb8-abea-dd6dfeb524bf.png">

###### You can remove the auto-termination. That means you can shut the cluster what ever time you want. The other way the cluster will be terminated 1 (changeable) hours.
<img width="961" alt="Ekran Resmi 2022-03-15 21 13 45" src="https://user-images.githubusercontent.com/91700155/158468379-23a12095-fbdd-4941-9889-a55bebb67e93.png">

##### Step-3
###### Where do you keep your log files? We will choose the log file which is created in S3 folder.
<img width="1015" alt="Ekran Resmi 2022-03-15 21 15 34" src="https://user-images.githubusercontent.com/91700155/158471305-358e05c0-db5f-4042-8d75-dc1ef12e8901.png">
<img width="839" alt="Ekran Resmi 2022-03-15 21 18 35" src="https://user-images.githubusercontent.com/91700155/158468417-d3ca6ec4-e4d6-4a91-baeb-e03673178eaf.png">

##### Step-4
###### Security Options for Ec2 Key Pair choose choose EC2 key-pair you created earlier.
Click Create Cluster.
<img width="849" alt="Ekran Resmi 2022-03-15 21 20 05" src="https://user-images.githubusercontent.com/91700155/158468532-ff1a63ac-238d-4b71-867a-581c12a210e0.png">

  
##### Now your cluster should be in the process of being created. This can take a few minutes to complete. The cluster will be in waiting state once it completes.
<img width="1077" alt="Ekran Resmi 2022-03-15 21 21 22" src="https://user-images.githubusercontent.com/91700155/158468571-3f875023-85d9-4e26-b481-30e4eaf8c1d0.png">



#### B- SSH Into The Cluster
##### In the “Summary” tab, scroll down to the “Security and access” section and select the security group shown for Security Group for Master. 
<img width="1122" alt="Ekran Resmi 2022-03-15 21 29 06" src="https://user-images.githubusercontent.com/91700155/158468600-399e082e-009c-429b-9746-66e1046479c9.png">

##### Select the security group for “ElasticMapReduce-master” and click "Edit Inbound rules"
<img width="1373" alt="Ekran Resmi 2022-03-15 21 29 43" src="https://user-images.githubusercontent.com/91700155/158468710-7116b58d-cd29-4f98-9ec1-f98c884c5462.png">
  
##### Click on Add rule:
Add a rule that allows SSH Anywhere or Your IP
<img width="1320" alt="Ekran Resmi 2022-03-15 21 30 54" src="https://user-images.githubusercontent.com/91700155/158472650-141c9fec-0847-463c-ac51-41d8921c5fe4.png">
  
#####  Go back to "Summary tab". Once the cluster shows as “Waiting – Cluster ready” open up a terminal or SSH client and SSH into the master node. Obtain the SSH connection information from your cluster summary tab. 
<img width="1126" alt="Ekran Resmi 2022-03-15 21 37 58" src="https://user-images.githubusercontent.com/91700155/158468738-0a8af253-902c-429b-85e7-7fad246f936a.png">

##### Click on Connect to the Master Node Using SSH
<img width="782" alt="Ekran Resmi 2022-03-15 21 38 59" src="https://user-images.githubusercontent.com/91700155/158468784-63c795df-8835-4bea-ad01-7c2904c5bc91.png">
##### Shell on your local machine
```console
ssh -i <your key pair> hadoop@<emr master public dns address>
```
###### For me:
```console
chmod 400 mykeypair-emr.pem
ssh -i /Users/sedaatalay/Desktop/mykeypair-emr.pem hadoop@ec2-35-158-132-255.eu-central-1.compute.amazonaws.com
```
<img width="749" alt="Ekran Resmi 2022-03-15 21 43 39" src="https://user-images.githubusercontent.com/91700155/158468833-8244a45f-d45a-42aa-88b5-2370f6b078a6.png">

##### Show all nodes through YARN command.
  
###### It shows we have one node (the core node).
```console
yarn node -list -showDetails -all
``` 
<img width="875" alt="Ekran Resmi 2022-03-15 21 44 38" src="https://user-images.githubusercontent.com/91700155/158468861-1b4f48db-1277-4427-b165-42394a71859d.png">

###### To see the cluster details.
```console
yarn cluster -lnl
``` 
<img width="1013" alt="Ekran Resmi 2022-03-15 21 46 52" src="https://user-images.githubusercontent.com/91700155/158468870-7220b6ab-1155-444c-bd3f-b1a0902843f4.png">
  
##### To see the yarn command.
```console
yarn
``` 
<img width="675" alt="Ekran Resmi 2022-03-15 21 47 31" src="https://user-images.githubusercontent.com/91700155/158474003-68562f70-3d26-4dbf-89b6-15cfac1ad67f.png">

  

<p>  <br />
</p>

#### Thank you :)
  
<p>  <br />
</p>

 ## Seda Atalay
