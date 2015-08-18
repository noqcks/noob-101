Title: High-Level Knowledge
Date: 2015-07-15 13:01
Modified: 2015-07-15 13:01
Category: skynet
Authors: JScott, Nikki Martinez
Summary: How all the pieces of the puzzle work together

## Locally

Skeleton and git-ready will help you create and modify roles and playbooks. You will commit these to your fork on GitHub and create a Pull Request to get the changed reviewed and finalized. Finalized changes should be synced to Forge's S3 Bucket and Ansible Galaxy, which is currently manual. Additionally, you may have to use GitHub to populate the Bucket if it doesn't exist.

Install `telusdigital.aws-infrastructure` via Ansible Galaxy and run the appropriate playbook's `infrastructure.yml` to start creating a remote VPC.

## Remote

When an EC2 Server starts, aws-infrastructure tell AWS to tell the server to download and run Forge. The infrastructure playbook will generate EC2 tags which tell Forge what playbooks to download and install. All roles are downloaded from Ansible Galaxy. Once Forge is done, you have a fully configured server.

Enjoy!

![Photo]({filename}/images/synergy.jpg)
