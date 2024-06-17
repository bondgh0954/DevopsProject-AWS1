# DevopsProject-AWS1

# Demo Project

  Deploy Web Application on EC2 instance(manually)

# Technologies used
   AWS
   Docker
   Linux

# Project Description
  1. Create and configure an EC2 instance on AWS
  2. Install Docker on remote EC2 instance
  3. Deploy Docker image from private Docker repository on EC2 instance

# Detailed Description of Project
   Creating EC2 instance from UI
  login to aws account as IAM user

  Navigate to services and select compute and then EC2
  select lunch instance

  Name eg. server-instance
  (other tags can be added)

  Application and OS images
  select one operating system from the list
  eg. 'Amazon Linux

  Create key pair
  securely save the created key pair (.pem file)


  Configure network settings
  security group 
  close all ports and open only ports where application will be running
  configure ssh port 22 with your ip address

  click 'lunch instance after all configuration is set'

  # Connecting to the EC2 instance created

  copy the key pair of the EC2 instance to the .ssh directory in the home directory of your device
  ( mv downloads/key-pair.pem ~/.ssh )

  change the file permission of the key pair to allow only ec2 user to have read access
  (chmod 4000 ~/.ssh/key-pair.pem)

  ssh into the server or EC2 instance
  (ssh -i ~/.ssh/key-pair.pem ec2-user@publicIp)
    

    
  

  
  

  
  
  
  
  
