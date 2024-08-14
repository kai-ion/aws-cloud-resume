# AWS-CLOUD-RESUME-CHALLENGE


This is my attempt at cloud resume challenge in AWS.
What is Cloud Resume Challenge? - [The Cloud Resume Challenge](https://cloudresumechallenge.dev/) is a multiple-step resume project which helps build and demonstrate skills fundamental to pursuing a career in Cloud. The project was published by Forrest Brazeal.


**Services Used**:

- S3
- AWS CloudFront
- Certificate Manager
- AWS Lambda
- Dynamo DB
- GitHub Actions
- Terraform

## [Live Demo using github 🔗](https://kai-ion.github.io/aws-cloud-resume/)
## [Live Demo using AWS 🔗](https://cloudresume.kaiion.com/)

<br>

# Setup Tutorial

- [Static Website](#static-website)
- [Custom Domain](#custom-domain)
- [S3 Bucket](#s3-bucket)
- [Cloundfront]()
- [SSL Certificate]()
- [Route53 DNS Management]()
- [Javascript - Visitor Counter]()
- [DynamoDB]()
- [AWS Lambda Function]()
- [AWS Lambda Function connection]()
- [Git and CI/CD]()

<br>

## Static Website
I created my static website based on a template

![image](assets/img/website.PNG)

<br>

## Custom Domain

- I used namecheap to purchase one domain and then I also used AWS Route 53 to purchase a domain
    - https://www.namecheap.com/
    - https://aws.amazon.com/route53/ 
- You can see below that I purchased the domain kaiion.com on namecheap and piguit.com on Route 53

![image](assets/img/Namecheap.PNG)

![image](assets/img/Route53%20Domain.PNG)

<br>

## S3 Bucket
1. First you have to create an AWS account which is pretty straight forward
2. Log onto your AWS console, search and click on “S3”
3. Then click on the “Create bucket” button

![image](assets/img/S3%20bucket.webp)

4. When choosing a name for the bucket, there are a list of naming conventions on S3
    - Must be globally unique
    - Must be DNS-compliant, meaning they can only contain lowercase letters, numbers, periods (.), and hyphens (-)
    - Bucket names should not contain underscores (_), uppercase letters, spaces, or any special characters
    - Bucket names should be between 3 and 63 characters long
    - [Reference to the S3 doc for naming convention](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucketnamingrules.html?icmpid=docs_amazons3_console)
5. You can choose your region, I selected “us-east-1” as the region for the bucket, and leave all other settings as default

![image](assets/img/bucket-creation.PNG)

![image](assets/img/bucket-creation-2.webp)

6. Click on the “Create bucket” button at the bottom

![image](assets/img/bucket-creation-3.webp)

7. You will see your bucket created along with the corresponding message

![image](assets/img/bucket-creation-4.PNG)

8. Navigate into the created bucket and proceed to upload your static website files
    - Click on “Upload” button
    - Click on “Add files” to upload them into the bucket
    - Once the files appear in the bucket, click on the “Upload” button to proceed with the upload process
    - Our website is almost ready to be hosted

![image](assets/img/bucket-upload.PNG)

![image](assets/img/bucket-upload-2.PNG)
