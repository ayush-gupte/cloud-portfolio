# Project — Serverless AI Image Labelling Pipeline on AWS

## Overview
This project demonstrates how to build a serverless AI-powered image analysis pipeline on AWS using Amazon S3, AWS Lambda, and Amazon Rekognition. When an image is uploaded to the S3 bucket, it automatically triggers a Lambda function which sends the image to Rekognition for label detection. The detected labels along with confidence scores are processed and stored back in the S3 bucket in JSON format.

## Architecture

![Project Architecture](Screenshots/00%20Project%20Architecture.png)

## Implementation Steps

### 1. Create S3 Bucket
An Amazon S3 bucket is created to store images that will be uploaded and analyzed by the AI pipeline.

![S3 Bucket Created](Screenshots/01%20S3%20Bucket%20Created.png)

---

### 2. Create Lambda Function
An AWS Lambda function is created which will process uploaded images and interact with the Rekognition service.

![Lambda Function Created](Screenshots/02%20Lambda%20Function%20Created.png)

---

### 3. Adding Premissions in Lambda Role
The Lambda execution role is updated with permissions to access S3 and Amazon Rekognition so the function can read images and store analysis results.

![Adding Premissions](Screenshots/03%20Adding%20Premissions%20in%20Lambda%20Role.png)

---

### 4. Code Updated in Lambda Function
The Lambda function code is written in Python to receive the uploaded image event, send the image to Rekognition, detect labels, and generate a structured JSON output.

![Code Updated](Screenshots/04%20Code%20Updated%20in%20Lambda%20Function.png)

---

### 5. Adding Trigger in Lambda Function
An S3 event trigger is configured so that whenever a new image is uploaded to the bucket, the Lambda function is automatically executed.

![Trigger Added](Screenshots/05%20Adding%20Trigger%20in%20Lambda%20Function.png)

---

### 6. Uploading File in S3
A test image is uploaded into the S3 bucket to initiate the automated image analysis pipeline.

![Uploading File](Screenshots/06%20Uploading%20File%20in%20S3.png)

---

### 7. Image used in S3
The uploaded image is verified in the S3 bucket before it is processed by the Lambda function.

![Image Used](Screenshots/07%20Image%20used%20in%20S3.png)

---

### 8. Result In CloudWatch Logs
CloudWatch logs confirm that the Lambda function was triggered successfully and the Rekognition API analyzed the image.

![CloudWatch Logs](Screenshots/08%20Result%20In%20CloudWatch%20Logs.png)

---

### 9. Results Stored Back in S3 in JSON format
The labels detected by Rekognition along with their confidence scores are stored back into the S3 bucket as a JSON file.

![Results Stored](Screenshots/09%20Results%20Stored%20Back%20in%20S3%20in%20JSON%20format.png)

---

### 10. Downloaded Result to local machine
The generated JSON output file is downloaded locally to verify the label detection results.

![Downloaded Result](Screenshots/10%20Downloaded%20Result%20to%20local%20machine.png)

---

## Learning Outcomes
- Implemented a serverless event-driven architecture using AWS services
- Integrated Amazon Rekognition for automated AI image analysis
- Automated workflows using S3 triggers and AWS Lambda
- Stored structured AI analysis results in JSON format
- Used CloudWatch logs for monitoring and debugging serverless applications
