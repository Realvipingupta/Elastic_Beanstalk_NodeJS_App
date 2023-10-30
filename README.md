# Node.js Application Deployment to Elastic Beanstalk using CloudFormation

![GitHub](https://img.shields.io/badge/license-MIT-blue.svg)

This repository contains a Node.js application that can be deployed to Elastic Beanstalk using CloudFormation. The application is a simple example of how to use CloudFormation to deploy a Node.js application to Elastic Beanstalk behind an Elastic Load Balancer and an Auto Scaling Group.

## Prerequisites

Before you get started, make sure you have the following prerequisites in place:

- An AWS account with access to Elastic Beanstalk and other services like- Elastic Load Balancer or RDS as per your requirement.
- A sample application bundled into a zip file, Like - I'm using NodeJS application.
- A VPC network.
- An IAM role with the necessary permissions for Elastic Beanstalk to deploy your application [Optional].
- Make sure you've S3 bucket created and required code ZIP available.

## Instructions

Follow these steps to deploy your Node.js application to Elastic Beanstalk using CloudFormation:

1. Upload the CloudFormation template and the application source bundle to an S3 bucket.

2. Create a new CloudFormation stack using the template, specifying the following parameters:

   - VpcID: The ID of your VPC.
   - EC2SubnetID: The ID of the subnet where you want to launch your EC2 instances.
   - AppEnvironment: The environment of your Elastic Beanstalk application (e.g., staging, production).
   - EC2InstanceType: The instance type for your EC2 instances.
   - LoadBalancerSubnetID: The ID of the subnet where you want to deploy your Elastic Load Balancer (ELB).
   - LoadBalancerVisibility: The visibility of your ELB (public or private).
   - AppSolutionStackType: The type of solution stack to use for your Elastic Beanstalk application. This parameter specifies the operating system, programming language, and web server that will be used to deploy your application.
   - S3BucketName: The name of the S3 bucket where your application source code is stored.
   - S3BucketFileName: The name of the S3 object that contains your application source code.

3. Wait for the CloudFormation stack to create all of the necessary resources.

4. Once your application is deployed, you can access it at the URL of your ELB.

## Scaling Policies

The CloudFormation template includes the following scaling policies for the Auto Scaling Group:

- Upper threshold: 80% CPU utilization
- Breach duration: 5 minutes
- Upper breach scale increment: 1 instance
- Lower threshold: 30% CPU utilization
- Lower breach scale increment: -1 instance

These policies will ensure that your application can handle varying loads by automatically scaling the number of EC2 instances up or down based on CPU utilization.

## Troubleshooting

If you have any problems deploying or running your application, please consult the AWS documentation for Elastic Beanstalk.

## Additional Notes

- You can customize the CloudFormation template to meet your specific needs. For example, you can change the scaling policies, the instance type, or the solution stack name.
- You can also use the CloudFormation template to deploy other types of applications, such as Java applications or Python applications.
- You can use my NodeJS Code reference available in this repository with name - nodejs.zip

## Contributing

If you would like to contribute to this project, please feel free to submit a pull request.

## License

This project is licensed under the MIT License.
