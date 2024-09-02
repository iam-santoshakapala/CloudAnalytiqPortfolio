# Hosting Static Website Using AWS S3

Welcome to this concise guide on hosting a static website using AWS S3 (Simple Storage Service)

## :rocket: Introduction

Hosting a static website on AWS S3 is a great way to get a site up and running quickly and cost-effectively. Here's a
step-by-step guide to help you through the process.

## :scroll: Step-by-Step Guide

Follow these steps to host your static website on AWS S3:

1. **Access AWS Console**

   Go to your AWS console and search for "S3" in the search bar, then select "S3" when it appears.

2. **Create a Bucket**

    - Click on "Create bucket."
    - Provide a unique bucket name(e.g., `cloudanalytiq.com`) for your website. Bucket names need to be globally
      unique, so choose something specific to you or your project.
    - Select an AWS Region where you want to store your files. Choose a region close to your target audience to reduce
      latency.

3. **Configure Bucket Settings**

    - Unselect "Block all public access" to allow internet users to access your website.
    - Click on "Create bucket" at the bottom.

4. **Select Your Bucket**

   Once created, select your bucket from the list.

5. **Configure the Bucket for Static Web Hosting**

    - Under the "Properties" tab, scroll down to "Static web hosting" and click on "Edit."
    - Click on "Enable" and select "Host a static website." Choose the default home page (index.html) for your site.

6. **Set Up Error Handling (Optional)**

    - Enter the error page(error.html), then click "Save changes."

7. **Endpoint Creation**

   When "Static website hosting" is enabled, the bucket endpoint is created.

    8. **Bucket Policy for File Access**

        - Create a bucket policy to enable access to the files.
        - Navigate to the "Permissions" tab and under the "Bucket policy" section, enter the provided policy, ensuring
          to
          change the Resource to your bucket's ARN followed by "/*".

        - Example:

          `{
          "Version": "2012-10-17",
          "Statement": [
          {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::cloudanalytiq.com/*"
          }
          ]
          }`

9. **Upload Your Website**

   Create and upload your website files, including the "index.html" and "error.html" file as specified in step 8.

10. **Final Configuration**

    - Navigate to the "Properties" tab and load the bucket's endpoint. The "index.html" file will serve as the home
      page.
    - In case of an error (e.g., the index file is not available), the "error.html" page will be returned at the
      endpoint.

11. **(Optional) Set Up a Custom Domain with Route 53**

    If you want to use a custom domain name:

    - Purchase a domain if you don’t already have one (you can use AWS Route 53 or another domain registrar like
      GoDaddy).
    - Create a Route 53 hosted zone for your domain and configure the DNS settings to point to your S3 bucket’s
      endpoint.
    - Update your bucket name to match your custom domain (e.g., `cloudanalytiq.com`), and configure S3 to use this
      domain for static website hosting.
    - Update your DNS records to include an alias record pointing to the S3 bucket endpoint.

12. **(Optional) Enable HTTPS with CloudFront**

    To serve your site over HTTPS:

    - Create a CloudFront distribution and configure it to use your S3 bucket as the origin.
    - Request or import an SSL/TLS certificate via AWS Certificate Manager (ACM).
    - Associate the certificate with your CloudFront distribution and configure CloudFront settings for HTTPS.
    - Update your DNS records to point to the CloudFront distribution URL.

## :page_with_curl: Sample Website Pages

The article includes sample website pages for your reference:

- **index.html**: A basic static web page with AWS S3-themed content.
- **error.html**: A custom error page (404) for handling missing files.

## :tada: Conclusion

With these steps, you can easily host your static website on AWS S3, benefiting from its simplicity, speed, and
cost-effectiveness. Have fun hosting your website!

If you have any questions, feedback, or collaboration opportunities, please feel free to reach out to me. You can
contact me via email at [santosha.kapala@yahoo.com](mailto:santosha.kapala@yahoo.com)
---

*Author: [Santosha Kapala](https://www.linkedin.com/in/santosha-kapala-703a9b25/)*