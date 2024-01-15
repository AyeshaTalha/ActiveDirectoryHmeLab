# ActiveDirectoryHomeLab
<h2>Description:</h2>
This project guide outlines the steps to set up an Active Directory (AD) home lab using VirtualBox, incorporating a Domain Controller (DC) with two network adapters. The DC will be configured to connect to the internet through one adapter using DHCP and establish an internal network using the second adapter with a static IP address (172.16.0.1). A client machine will connect to the internal network through the DC, allowing internet access through the DC.

<h2>Project Architecture:</h2>
<p align="center">
<img src=https://imgur.com/xm5huv7.png" height="80%" width="80%">



<h2> Pre-Requisites:</h2>
Before starting, ensure you have the following:

VirtualBox installed on your host machine.
Adequate system resources (RAM, CPU) for running multiple virtual machines.
Windows Server installation ISO (e.g., Windows Server 2009 and 2010).

<h2>Project Workflow:</h2>

1. If you dont already have Virtual Box downloaded then go to virtualbox download and download the correct software according to the Operating System you are using. After downloading the Virtual Box, also download the extension pack for the Virtual Box.

<p align="center">
<img src=https://imgur.com/DRa0Hfv.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/GmKrO9q.png" height="80%" width="80%">
<br />

2. We are going to use Windows Server 2009 and Windows Server 2010 for our DC machine and Client1 machine respectively. To use these, we need to download the ISO's of these server. Go to windows server 2009 download and download the ISO's for both the servers. Make sure you remember the location where you're going to save these downloads. We are going to need that later.           
<img src="https://imgur.com/v56YnjO.png" height="80%" width="80%">
<br />



3. First, let us create the first Virtual Machine - DC. 
<p align="center">
<img src="https://imgur.com/XqZrgem.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/4GSgo4a.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/ZBPB2LS.png" height="80%" width="80%">
<br />

4. We need to create a Lamda Function that will process our math functionality. From AWS Console, navigate to AWS Lamda. Click on New function. We are going to author this from scratch. Enter thr name of thr Function, Runtime as the latest version of Python and click on Create Function.On the main page of Lamda, scroll down to the Code block. The code for this Lamda Function is given in the LamdaFunctionOriginal file above. Just copy and paste the code. Click on Deploy and we are done.
<p align="center">
<img src="https://imgur.com/XnvzGhE.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/b8ejCFq.png" height="80%" width="80%">
<br />

5. Now, we need something to invoke our Math Functionality. For this, we will use API Gateway. This is a core functionality in AWS which we can use to create our own APIs. In a Serverless Architrcture, it is the perfect way to invoke our Lamda Function. From the AWS Console, navigate to API Gateway and Click on Create API. We are going to use a REST API. Give it a name and click on Create API. 
<p align="center">
<img src="https://imgur.com/vCsjcMa.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/2U90adI.png" height="80%" width="80%">
<br />

6. Click on the API created. On the lefthand side, click on Resources. On the righthand side, click on "/". From thr Actions menu, select Create Method. The type of method will be POST. Enter the Lamda Function name and create the POST method as shown below:
<p align="center">
<img src="https://imgur.com/YTPA3rb.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/8a0masw.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/srGDfkU.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/srGDfkU.png" height="80%" width="80%">
<br />

7. Next, we must Enable CORS (Cross Origin Resourse Sharing) so that our website can interact with the lamda function. To do so, click on the POST method and from Actions menu select Enable CORS. Click on Deploy API to deploy and enter the Deployment stage as dev. Copy the Invoke URL and keep it handy. We will be using it later.
<p align="center">
<img src="https://imgur.com/SItVLAs.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/jXU9YV6.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/izfqvWx.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/rebURyF.png" height="80%" width="80%">
<br />

8. Now we need to setup a database to store the results. We will use DynamoDB for this. Navigate to DynamoDB and Click on Create Table. Enter the name and create table. Copy the ARN of this table.
<p align="center">
<img src="https://imgur.com/WKxFXsx.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/MZlcvLu.png" height="80%" width="80%">
<br />

9. Next, we have to give our Lamda Function the permission to write results to the DynamoDB table. Navigate back to the our Lamda Function and Scroll down to the Configuration section. Click on the execution role and select add inline policy. Name the policy and click on JSON. The code for this policy is given above in the ExecutionRolePolicyJSON file. Copy and paste the code and create the policy. Make sure you enter the ARN of the Table you created in the poilcy. 
<p align="center">
<img src="https://imgur.com/My4oAHR.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/yYlLunx.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/X0lQ9zG.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/i9fiX9S.png" height="80%" width="80%">
<br />

10. Navigate to the Code tab of the Lamda Function. We need to make some changes to our code so that the Lamda Function can write the results to the table. It wasn't doing that before. The updated code is given above in the LamdaFunctionFinal file. Copy and paste the code and click on Delopy.
<p align="center">
<img src="https://imgur.com/YsAMw1C.png" height="80%" width="80%">
<br />

11. We must update our Index.html file in order to invoke the API from our website. Copy the code from Index.html file above and paste it in your file. Make sure you add your API gateway endpoint.   Compress the file and add it to our Amplify website.
<p align="center">
<img src="https://imgur.com/itA0zVR.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/K3urd8N.png" height="80%" width="80%">
<br />

12. Click on the URL of the website and there it is. Enter a Base number and an exponent number and hit Calculate. It will give the result.
<p align="center">
<img src="https://imgur.com/XDJm1gT.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/1tqGACw.png" height="80%" width="80%">
<br />


<h2>Benefits of AWS Serverless Web Application:</h2>

- Scalability: The serverless architecture allows the web application to scale automatically based on demand, ensuring optimal performance even during high traffic periods.

- Cost-effectiveness: With serverless, you only pay for the actual usage of resources, eliminating the need for provisioning and managing servers, which can result in cost savings.

- High availability: AWS services, such as Lambda and DynamoDB, are designed to be highly available and fault-tolerant, ensuring the web application remains accessible even in the event of failures.

- Reduced operational overhead: Serverless architecture offloads the operational tasks, such as server management, to AWS, allowing developers to focus more on application development and business logic.
<br/>
