# aws-s3-mfa-delete

**Create a S3 bucket**

Navigate to S3 console and create a new S3 bucket with Versioning enabled.

<img width="875" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/8e9ebc85-4c75-4fe1-93e9-f999a1b45833">

By default, We can't able to enable MFA through AWS console. So we have to enable the MFA for S3 bucket with the help of AWS CLI.

Make ensure that MFA should enable for your IAM user or root user (If you are using root account)

**Configure AWS CLI**

Create accesskey and secretkey for your IAM user and configure it in your local system.

Here I'm using AWS CloudShell, So i will do configure with accesskey and secretkey.

**Access CloudShell**

Configure aws cli in CloudShell

<img width="421" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/d72a84ad-dbde-4f92-a937-025938a451d0">

After configuration, I can able to list my s3 buckets from CloudShell console.

<img width="851" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/6d3f01dc-0180-4cad-9ee0-d865d822a384">


**Enable MFA**

To enable a MFA for S3 bucket with below command.

# enable mfa delete

**aws s3api put-bucket-versioning --bucket <bucket-name> --versioning-configuration Status=Enabled,MFADelete=Enabled --mfa "arn-of-mfa-device mfa-code" --profile root-mfa-delete-demo**

<img width="944" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/07d27501-1ec6-47e7-b314-5775d4c51390">

You have to update the MFA ARN and your MFA code (from your device) in the command and enter it. Now MFA has been enabled to specific S3 bucket.

<img width="890" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/982b9072-beb1-4500-aa8e-95a90e21ede5">

**Upload object**

I have uploaded one object to s3 bucket.

<img width="692" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/3e862877-8a8a-405e-9c51-d5ac7cc3ff04">

**Remember, I already enabled Versioning while creating S3 bucket.**

<img width="845" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/e10de7c2-a562-459a-b78b-26eff8cb16f0">

Try to delete your object. 

<img width="937" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/d10d2208-a39d-43e7-a88d-7ca0240cceaf">

Perfect! Object has been deleted as we expected.

Now try to delete the Versioning of Object. I'm going to delete this specific Version of Object.

<img width="868" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/f14ec86a-2b23-4de6-b1ca-388d5a7e9a1a">

Hey, You can see here, Without MFA you cant able to delete the Versioning.

<img width="743" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/ef5eec07-7feb-40ac-826c-a241cfa86e72">

To do delete the Versioning of Object, you should disable the MFA through AWS CLI commands.

# disable mfa delete

**aws s3api put-bucket-versioning --bucket <bucket-name> --versioning-configuration Status=Enabled,MFADelete=Disabled --mfa "arn-of-mfa-device mfa-code" --profile root-mfa-delete-demo**

<img width="935" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/6bd26ca4-8ce8-4e0c-ab56-25eb86cbd1b2">

**Now, MFA has been disabled from specific s3 bucket.**

<img width="883" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/bf3f28c6-a76a-4422-8fde-056c33dd7ebb">

**Now, You can delete the S3 object versioning from AWS S3 console.**

<img width="852" alt="image" src="https://github.com/kohlidevops/aws-s3-mfa-delete/assets/100069489/73c869d0-0fcf-4bf8-95b4-6c16857a8434">

**That's it. Please remove the accesskey and secretkey from your console once you tested.**




