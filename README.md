# Learn Terraform Provisioning
Companion code repository for learning to provision Terraform instances with Packer

Follow along on the [HashiCorp Learn platform](https://learn.hashicorp.com/tutorials/terraform/packer?in=terraform/provision)


I. Create a local SSH key

`$ ssh-keygen -t rsa -C "your_email@example.com" -f ./tf-packer`

II. Packer image

- `image.pkr.hcl` - Packer configuration defines the parameters of the image you want to build.

- The `locals` block creates a formatted timestamp to keep your AMI name unique.

- The `source` block generates a template for your AMI.

- The source `amazon-ebs` declares this image will be created in AWS and uses Elastic Block Storage. 

- `build` block builds out your instances with specific scripts or files. Your build is based on the previously declared `source` as the type of AMI.

- The `provisioner` blocks copy your key to the image and run your setup script.

IV. Build Packer image

`$ packer build image.pkr.hcl`
