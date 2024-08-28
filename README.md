# COSC55
# Final Project: Maddy and Annabella

## Project Description
This project is focused on deploying and testing a cloud environment for our organization, following the plan detailed in Milestone 2: System Build Plan. The project encompasses setting up a public-facing webpage, configuring secure private instances, managing SSH keys, establishing an S3 bucket for document storage, and building a secure Virtual Private Cloud (VPC) network. Each component has been meticulously configured to ensure security, accessibility, and scalability.

## Key Features
### Website hosted on Ubuntu AMI
The public webpage is hosted on an Ubuntu Amazon Machine Image (AMI) within our AWS environment. The decision to use Ubuntu over RedHat was based on its flexibility and compatibility with the software required for our application.
### S3 Bucket Link
The webpage includes a clickable link that directs users to our S3 bucket. This bucket currently allows public access but will be restricted in future updates to ensure only authorized users can upload or download documents. An S3 bucket has been established to store important company documents. This bucket currently allows public access, but future phases of the project will implement stricter access controls to secure the data. Documents can be uploaded to the S3 bucket from the private instance, ensuring that sensitive data is handled within a secure environment
## Configurations
### Private Instance on Private Subnet
A private instance has been set up on a dedicated private subnet within our VPC. This instance is configured to handle sensitive operations, such as uploading documents to the S3 bucket.
### Bastion Host 
A Bastion host has been configured on the public subnet of our VPC. This host serves as an intermediary for SSH access to the private instance. The Bastion host is the only entry point to the private instance, ensuring that all traffic to the private instance is secured and controlled within our VPC.
### SSH Key Management
A new master SSH key was generated for managing the public webpage. This key is securely stored on authorized computers and is used to SSH into the Ubuntu server hosting the webpage. The SSH key is critical for maintaining secure and controlled access to the public instance, ensuring that only authorized users can make changes to the webpage.
### VPC and Subnets
A Virtual Private Cloud (VPC) has been created to house all components of the project. The VPC includes a public subnet for the Bastion host and a private subnet for the private instance. Routes have been configured to control traffic between the subnets and the internet. An internet gateway allows the public subnet to access the internet, while an S3 VPC endpoint enables secure communication between the private subnet and the S3 bucket.
### Security Groups
A security group has been configured for the public Ubuntu server, allowing HTTP/HTTPS access from any IP address. SSH access is also permitted, enabling authorized users to manage the server. While the webpage is publicly accessible, we have designed the security rules to prevent unauthorized document uploads to the S3 bucket from this instance

