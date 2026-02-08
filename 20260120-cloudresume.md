---
layout: default
---
[Back Home](./index.md)
 

# AWS Cloud Resume

Date: 1/20/2026
<br/><br/>

## DESCRIPTION

The AWS Cloud Resume Project is a comprehensive, full-stack serverless application designed to showcase technical expertise by transforming a standard resume into an interactive document hosted by AWS. The architecture involves hosting a responsive frontend on Amazon S3, which is then globally distributed via Amazon CloudFront for low-latency delivery and secured with AWS Certificate Manager. To provide interactive functionality, the project incorporates a visitor counter powered by a backend API. This backend leverages Amazon API Gateway to trigger AWS Lambda functions that interact with an Amazon DynamoDB table, creating a cohesive, live environment that demonstrates the power of cloud-native development.

Completing this project has helped me build a robust foundation in modern cloud engineering and DevOps practices. I have learned a great deal about AWS services beyond training for certifications, by providing real-world hands-on experience with core AWS services. It has also given me a greater understanding of CI/CD pipelines through using GitHub Actions for automated testing and deployment. Beyond learning AWS specific services, this project has also helped me gain some familiarity in serverless logic, database management, and web security. By bridging the gap between theoretical certification and practical implementation, this project serves as a tangible demonstration of my ability to learn, deploy, and troubleshoot cloud solutions.
<br/><br/>

## AWS CLOUD RESUME PROJECT IMPLEMENTATION

# Parameters

1. Static website hosted on S3
2. Secure using HTTPS
3. Have a visitor counter
4. Include a generative AI feature
5. CI/CD pipeline using GitHub

# Step 1 - HTML, CSS, JS

I started with a simple HTML template and some prompt engineering to develop a style sheet and javascript to recreate my resume in html form with a style that felt pleasing and professional. At this point, the script only contained a placeholder for the AI chatbot and a visitor counter using LocalStorage.

# Step 2 - Create initial AWS Services - S3, Route 53, CloudFront

Using my previously created AWS account I made for study and exploration, I setup a new S3 bucket as a static website and uploaded the newly created webpage + assets. I tested that everything worked by pasting the S3 bucket address directly into a browser. Once confirmed, I removed all public access in preparation for using CloudFront as a more secure and faster method of accessing the webpage. I bought my domain through Route 53, 

# Step 3 - Create functional visitor counter - DynamoDB, Lambda / API Gateway, JS (with API trigger)



# Step 4 - Create GenAI Chatbot - Amazon Bedrock, Claude 3 Haiku



# Step 5 - Create CI/CD Pipeline using GitHub



<br/><br/>

#  
[Back Home](./index.md)

