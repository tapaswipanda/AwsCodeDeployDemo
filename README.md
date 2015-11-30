# AwsCodeDeployDemo
Code deployment for application running behind an AWS Elastic load balancer in an Auto Scaling environment.

I am assuming you have an existing application running having AWS ELB and auto-scaling set up.

### Steps for Code Deploy Set up with Github.

1. Install AWS CLI  - on any existing instance
2. Install Code Deploy agent  - on the same instance as step #1
3. Create IAM 2 role
    i) codeDeploy  - for Code Deploy service to talk to EC2 to get instance tags
    ii) Ec2CodeDeploy  - for IAM profile instance
4. Take an Image(AMI) of the Ec2 instance, same instance you used in step #1 and #2
5. Create a new lunch configuration with the newly created AMI with IAM instance profile(Ec2CodeDeploy), created in step #3
6. Update the existing ASG to use the new lunch configuration.
7. Create a new code Deploy Group and  Application and group for the new ASG.
8. Create a Code Deploy revision having integration with Github.
9. Deploy a revision.
10. Wait till the deployment status says successful and check your application for your changes.
