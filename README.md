

# Terraform AWS Infrastructure Setup

This project contains Terraform configurations for setting up a basic AWS infrastructure, including a VPC, public subnet, internet gateway, security group, and an EC2 instance.

## Prerequisites

Before using this project, make sure you have the following installed:

- [Terraform](https://www.terraform.io/downloads.html) (v0.12 or higher)
- AWS account with credentials properly set up in your environment. You can configure credentials using the AWS CLI or directly using environment variables:
  ```bash
  export AWS_ACCESS_KEY_ID=your_access_key
  export AWS_SECRET_ACCESS_KEY=your_secret_key
  ```

## Resources Created

This Terraform project creates the following resources:

1. **VPC**: A Virtual Private Cloud with CIDR `10.123.0.0/16`.
2. **Public Subnet**: A public subnet with CIDR `10.123.1.0/24` in the `us-west-2a` availability zone.
3. **Internet Gateway**: Allows instances in the VPC to connect to the internet.
4. **Route Table & Association**: A route table for the public subnet with a default route to the internet.
5. **Security Group**: Allows inbound access from a specific IP (`93.22.133.253/32`) and outbound access to all IPs.
6. **Key Pair**: A key pair is created using the public key stored at `C:/Users/hamza/.ssh/key.pub.txt`.
7. **EC2 Instance**: A t2.micro instance is created using an AMI and placed in the public subnet.

## How to Use

1. **Clone the repository:**
   ```bash
   git clone https://github.com/saadallh/Terraform-AWS-Infrastructure-Setup.git
   cd your-repo-name
   ```

2. **Initialize Terraform:**
   Initialize the working directory with all the necessary plugins:
   ```bash
   terraform init
   ```

3. **Plan the Infrastructure:**
   You can review the infrastructure changes by running:
   ```bash
   terraform plan
   ```

4. **Apply the Configuration:**
   To create the resources on AWS, run:
   ```bash
   terraform apply
   ```
   Confirm the prompt by typing `yes`.

5. **Destroy the Infrastructure:**
   When you're done with the infrastructure and want to clean up the resources, you can run:
   ```bash
   terraform destroy
   ```

## Customizing the Configuration

- **VPC and Subnet CIDR blocks**: Update the `cidr_block` in the `aws_vpc` and `aws_subnet` resources if needed.
- **Security Group**: Adjust the allowed IPs, protocols, and ports in the `aws_security_group` resource.
- **Key Pair**: Ensure the path to your public key is correct in the `aws_key_pair` resource.

## File Structure

```
.
├── main.tf                  # Main Terraform configuration
├── datasources.tf           # Data sources for AMI lookups
├── providers.tf             # Provider configuration for AWS
├── userdata.tpl             # User data script for EC2 instance initialization
```


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE.txt) file for details.

---

You can add this `README.md` file to your project for a clear guide on setting up the infrastructure using your Terraform code.
