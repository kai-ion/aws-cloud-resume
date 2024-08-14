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

## Cloudfront

1. Go to CloudFront resource by navigating through the search bar.

![image](assets/img/cloudfront-1.webp)

2. Click on “Create distribution” button.

![image](assets/img/cloudfront-2.webp)

3. Select your s3 bucket domain in “Origin Domain” section.

![image](assets/img/cloudfront-3.PNG)

4. “Create new OAC” after selected “Origin access control settings (recommended)” in “Origin access” section.
    - Origin type could be “S3”.

![image](assets/img/cloudfront-4.PNG)

5. In Viewer protocol policy select “HTTPS only”.

![image](assets/img/cloudfront-5.PNG)

6. Scroll down to “Cache key and origin requests” and set next values.

![image](assets/img/cloudfront-6.PNG)

7. In my case I turn off WAF (Web Application Firewall) to save money

![image](assets/img/cloudfront-7.PNG)

8. Add /index.html to “Default root Object” field and click create distribution.

![image](assets/img/cloudfront-8.PNG)

9. When the distribution is created, you may receive a notification stating that The S3 bucket policy needs to be updated. In this case, click on the “Copy policies” button and add the copied policies to your S3 bucket’s policies.

![image](assets/img/cloudfront-9.PNG)

10. Open the S3 bucket you created earlier and navigate to the “Permissions” tab. Scroll down to the “Bucket Policies” section and click on the “Edit” button.
    - Paste your policies and click on “Save changes”

![image](assets/img/s3-bucket-policy.PNG)

![image](assets/img/s3-bucket-policy-2.PNG)

11. Go to your CloudFront distribution “Error pages” tab and create error responses for 403 and 404.

![image](assets/img/cloudfront-10.PNG)

![image](assets/img/cloudfront-11.PNG)

12. Back in the General tab, under Details section you can see a Distribution domain name, you can now copy and paste that link into your browser to see your website

![image](assets/img/cloudfront-12.PNG)

![image](assets/img/cloudfront-13.PNG)

## SSL Certificate

1. Navigate to AWS Certificate Manager (ACM) and select request
    - Click on “Next” and proceed to fill your domain name

![image](assets/img/SSL-1.PNG)

![image](assets/img/SSL-2.PNG)

2. In this case, I am requesting a wildcard certificate
    - A SSL/TLS Wildcard certificate is a single certificate with a wildcard character (*) in the domain name field. This allows the certificate to secure multiple sub domain names (hosts) pertaining to the same base domain.
    - For example, a wildcard certificate for *.(domainname).com, could be used for www.(domainname).com, mail.(domainname).com, store.(domainname).com, in addition to any additional sub domain name in the (domainname).com.

![image](assets/img/SSL-3.PNG)

3. For the validation method, I am using email validation because it is easier for me

![image](assets/img/SSL-4.PNG)

4. “Request” button to get your certificate
    - In my case I received an email to verify the SSL certificate
    - After awhile you should see the status changed to Issued

![image](assets/img/SSL-5.PNG)

5. Navigate back to your Cloudfront distribution to add the SSL certificate and alternate domain name (CNAME) record under general tab, section settings, and select edit
    - Add the alternate domain name you like
    - Add the SSL certificate
    - Select save changes

![image](assets/img/SSL-6.PNG)

![image](assets/img/SSL-7.PNG)

6. You should see that your cloudfront distribution settings updated with the new alternate domain names and custom ssl certificate

![image](assets/img/SSL-8.PNG)



