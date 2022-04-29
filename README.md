# linux_terraform


# Terraform/Ansible tips
The main use of Terraform is for writing infrastructure as code to manage public cloud resources such as AWS, GCP and Azure.

The infraestrusture can be entirely handled by Terraform or Ansible. Terraform uses cloud provider APIs to create infrastructure and basic configuration tasks are achieved using SSH. The same goes with Ansible – it uses SSH to perform all the required configuration tasks.

Terraform --> declarative code, meaning that it doesnt matter the order the code is written (most of times).
Ansible --> procedural code, meaning that the script is executed from top to bottom.

# Presentation terraform.

Installation of terraform. You can install it in linux, windows, mac.
Since I am working on mac. I install with mac using:
(The brew tap command adds more repositories to the list of formulae that Homebrew tracks, updates, and installs from.)
    . brew tap hashicorp/tap

    . brew install hashicorp/tap/terraform

Once installed check terraform version by 
    . terraform -v



# Create a cloud account. I used AWS
There is the possibility of using free account, even though you have to insert credit card details.



    . Implement connexion with api provider
        https://registry.terraform.io/providers/hashicorp/aws/latest/docs
      - For a safe connection with cloud. implement installation and configuration of AWS CLI. 
      - I create a python environment with conda  and install awscli
      EnvName: terraformEnv
      conda install -c conda-forge awscli
      - Checking aws --version
      - aws configure
        AWS Access Key ID [None]: 
        AWS Secret Access Key [None]: 
        Default region name [None]: us-east-1
        Default output format [None]: json
        (terraformEnv)Carloss-MacBook-Pro:~ crflorez$ aws iam get-user (to check user who create it).
        default root user is used.(didn't create an user in aws)

    . Implement connexion with api provider
      - Hit terraform init to see that connection is succesful and to download all the necessary plugins to interact with the API
      - You can track your changes with <terraform plan> command before actually running it.

    . Create a virtual server instance. Selecting the os and the type of instance(power assigned to that vm) I select t2.micro type since it is free:) Ubuntu distribution used.

    . Terraform as well as ansible track changes on the code and only apply differences. A difference though, between them is that with ansible as we said before the code is applied from top to bottom but in terraform it is 'intelligent enough' in many cases to relate tasks that are depending on others, so run them in correct order.
     . To delete instances you can do either terraform destroy to destroy the whole infrastructure or just delete or uncomment the part of code we don't want anymore.
Example grabbed from https://github.com/Sanjeev-Thiyagarajan/Terraform-Crash-Course/blob/master/main.tf

     . 1. Creation of VPC. virtual private cloud.
       2. Create Internet Gateway
       3. Create Custom Route Table
       4. Create a Subnet
       5. Associate subnet with Route Table
       6. Create Security Group to allow port 22,80,443
       7. Create a network interface with an ip in the subnet that was created in step 4
       8. Assign an elastic IP to the network interface created in step 7





