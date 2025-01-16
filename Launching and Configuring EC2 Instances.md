# **Launching and Configuring EC2 Instances**

## **Overview**

Amazon EC2 (Elastic Compute Cloud) provides scalable compute capacity in the cloud. It allows you to launch virtual servers, known as instances, to run applications and services. This lesson will walk you through launching and configuring EC2 instances in AWS.

By the end of this lesson, you will:

* Understand how to launch an EC2 instance.  
* Be familiar with EC2 instance types and configurations.  
* Learn to configure security groups, key pairs, and other instance settings.

---

## **Prerequisites**

Before starting this lesson, ensure that you have the following:

1. **An AWS Account**: You need an active AWS account.  
2. **IAM User with EC2 permissions**: Your IAM user should have permissions to launch and configure EC2 instances.  
3. **Basic understanding of AWS services**: Familiarity with the AWS Management Console and basic cloud concepts.

---

## **Steps to Launch and Configure an EC2 Instance**

### **Step 1: Log into the AWS Management Console**

1. Go to the [AWS Management Console](https://aws.amazon.com/console/).  
2. Sign in with your AWS credentials.

### **Step 2: Navigate to the EC2 Dashboard**

1. In the AWS Management Console, search for **EC2** in the search bar.  
2. Click on **EC2** to open the EC2 Dashboard.

### **Step 3: Launch a New EC2 Instance**

1. In the EC2 Dashboard, click on the **Launch Instance** button.  
2. Choose an **Amazon Machine Image (AMI)**:  
   * Select an AMI based on the operating system you want to use. For example, you can select the **Amazon Linux 2 AMI** for a basic Linux setup.  
3. Choose an **Instance Type**:  
   * Select an instance type based on your requirements (e.g., `t2.micro` for light workloads, eligible for the AWS Free Tier).  
   * Click **Next: Configure Instance Details**.  
4. Configure **Instance Details**:  
   * Select the **VPC** and **Subnet** where you want to launch the instance. If you're new to VPC, you can use the default settings.  
   * Leave other settings as default for now, or modify them based on your network requirements.  
   * Click **Next: Add Storage**.  
5. Configure **Storage**:  
   * You can add additional volumes if necessary, or simply use the default root volume.  
   * Click **Next: Add Tags**.  
6. **Add Tags** (Optional):  
   * Tags are key-value pairs to help organize your resources. For example, you can add a tag with Key: `Name` and Value: `MyFirstEC2Instance`.  
   * Click **Next: Configure Security Group**.  
7. **Configure Security Group**:  
   * A security group acts as a virtual firewall for your instance.  
   * Select **Create a new security group**.  
   * Add rules to allow specific traffic, such as:  
     * HTTP (Port 80\) for web traffic.  
     * SSH (Port 22\) to connect to your instance via terminal (if it's a Linux-based instance).  
     * If you're using a Windows instance, add **RDP (Port 3389\)** for remote desktop access.  
   * Click **Review and Launch**.  
8. **Review and Launch**:  
   * Review the configuration of your EC2 instance.  
   * Click **Launch**.

### **Step 4: Select or Create a Key Pair**

1. When prompted, select an existing key pair or create a new one.  
   * If creating a new key pair, name it and download the `.pem` file. This file is required to securely SSH into your EC2 instance.  
   * Click **Launch Instances** to complete the process.

### **Step 5: Access Your EC2 Instance**

After launching your EC2 instance, it may take a few minutes to become available. Once it's ready, follow these steps to access it:

1. **Get the Public IP**:  
   * In the EC2 Dashboard, navigate to **Instances**.  
   * Select your instance and note down the **Public IP** or **Public DNS**.  
2. **SSH into the Instance** (for Linux/Unix-based instances):  
   * Open a terminal on your local machine.  
   * Navigate to the directory where your `.pem` key is located.

Run the following command:  
bash  
Copy  
`ssh -i "your-key-pair.pem" ec2-user@your-instance-public-ip`

*   
  * Replace `your-key-pair.pem` with your key pair file and `your-instance-public-ip` with your EC2 instance's public IP address.  
3. **RDP into the Instance** (for Windows-based instances):  
   * Download the Remote Desktop Protocol (RDP) client.  
   * Obtain the **Administrator password** by clicking **Get Password** in the EC2 console (you will need your `.pem` key file).  
   * Connect to the instance using the RDP client and the credentials provided.

---

## **Configuring EC2 Instance Post-Launch**

### **1\. Security Group Configuration:**

* You can modify security group rules after launching an instance by going to the **Security Groups** section in the EC2 Dashboard.  
* Update rules to allow or deny traffic as needed.

### **2\. Elastic IP (Optional):**

* If you want a static IP address for your EC2 instance (which doesn’t change if you stop/start the instance), allocate an **Elastic IP** from the EC2 Dashboard and associate it with your instance.

### **3\. Monitoring with CloudWatch:**

* Amazon CloudWatch is automatically integrated with EC2 instances for monitoring CPU utilization, memory usage, disk I/O, and network activity.  
* Set up **CloudWatch Alarms** for resource usage thresholds to trigger notifications when metrics exceed set limits.

---

## **Next Steps and Further Reading**

Once you're comfortable launching and configuring EC2 instances, you can explore the following:

* **EC2 Auto Scaling**: Automatically scale your EC2 instances based on demand.  
* **Elastic Load Balancing (ELB)**: Distribute incoming traffic across multiple EC2 instances for better availability and fault tolerance.  
* **EC2 Spot Instances**: Save costs by using EC2 instances that can be interrupted and are available at a lower price.

For more details, refer to the [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/).

---

## **Conclusion**

You have successfully launched and configured an EC2 instance. You can now SSH into a Linux instance or RDP into a Windows instance, and configure your EC2 instance further as needed. From here, you can experiment with different configurations, security settings, and scaling options as you become more familiar with EC2.

