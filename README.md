# EC2 Jenkins Pipeline Project 
This project show how to automate the creation and management of AWS EC2 instances using a Jenkins pipeline. The pipeline can launch EC2 instances, configure them, and integrate with other infrastructure components as needed.

## Tools Used 
- AWS EC2 – to launch and manage instances
- Jenkins – to automate the pipeline
- GitHub – version control for Jenkinsfile and scripts
- AWS CLI / Shell Scripts – to execute commands on EC2
- Linux– environment for scripting

## Project Workflow
  1. Code Commit: Push your Jenkinsfile and scripts to GitHub.
  2. Pipeline Trigger: Jenkins detects changes and triggers the pipeline.
  3. EC2 Launch: The pipeline executes scripts or AWS CLI commands to launch EC2 instances.
  4. Configuration: Additional setup or configuration scripts run on the instances.
  5. Verification: Ensure EC2 instances are running and reachable.

## Project Structure

EC2-pipeline-project/
│
├── Jenkinsfile # Pipeline script for Jenkins
├── README.md
├── screenshots/ 
    ├── ec2_instances.png
    ├── jenkins_pipeline.png


## Challenges Faced While Creating EC2 via Jenkins Pipeline

While implementing the Jenkins pipeline to launch AWS EC2 instances, I encountered the following challenges:

1. **AWS Credentials Not Configured**
   - Jenkins pipeline failed because it could not locate AWS credentials.
   - Needed to configure either **IAM Role** (recommended) or **Access Keys** correctly on the Jenkins node.

2. **Key Pair Issues**
   - Pipeline failed with `InvalidKeyPair.NotFound`.
   - Challenge: Ensuring the correct **key pair exists** in AWS and is referenced properly in the pipeline.

3. **Subnet ID and Security Group Errors**
   - Errors like `InvalidSubnetID` or `InvalidGroup` occurred.
   - Needed to find the **correct subnet ID and security group ID** in the appropriate AWS region.

4. **First Pipeline Run Failure**
   - The initial run often failed due to syntax or configuration errors.
   - Sometimes, EC2 instances were partially created even when the Jenkins job failed.

5. **Multiple Instances Created**
   - Running the pipeline multiple times created extra EC2 instances.
   - Needed a way to **track and uniquely name instances** to avoid duplication.

6. **Termination Confusion**
   - Accidentally terminated main or other EC2 instances when cleaning up.
   - Learned to enable **termination protection** and carefully select instance IDs before termination.

7. **Pipeline Syntax and Multi-Line Commands**
   - Writing Groovy `sh` blocks for AWS CLI commands caused syntax errors.
   - Proper line continuation (`\`) and quoting were required for successful execution.

8. **Internet/Network Dependency**
   - AWS CLI commands require internet access from the Jenkins node.
   - Needed to ensure the EC2 running Jenkins had proper network connectivity.

9. **Output Verification**
   - Challenge: Understanding how to check EC2 creation status from Jenkins console output.
   - Cross-verification with **AWS Console** was necessary to confirm instance launch success.

## Conclusion

This project show the automation of AWS EC2 instance creation using Jenkins pipelines.  

Through this process, I learned how to:  
- Integrate Jenkins with AWS using IAM roles or credentials  
- Handle AWS resource creation, tagging, and cleanup programmatically  
- Debug pipeline errors and AWS CLI issues  
- Ensure proper network configuration, instance naming, and resource management  

Overall, this experience strengthened my understanding of **CI/CD workflows, cloud automation, and practical DevOps practices**, preparing me to efficiently manage cloud infrastructure in real-world scenarios.


