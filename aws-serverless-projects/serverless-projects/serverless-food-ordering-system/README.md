# Serverless Food Ordering System on AWS

## Overview

This project demonstrates the design and implementation of a **Serverless, Event-driven food ordering backend system** using AWS services.

The system simulates how real-world applications (like food delivery apps) process orders through multiple stages while ensuring scalability, automation, and real-time communication.

---

## 🛠️ Use Case

In real-world systems:
- Orders go through multiple lifecycle stages  
- Systems must handle multiple users simultaneously  
- Users expect real-time updates  
- Data must be stored reliably  
- Logs are required for debugging and monitoring  

---

## 💡 Solution

This project solves these problems by building a system that:

- Processes orders through multiple stages  
- Stores order data in a database  
- Sends real-time notifications to users  
- Stores order receipts for persistence  
- Simulates real users using EC2  
- Captures logs for monitoring  

---

## 🧱 Architecture

![Architecture](Screenshots/00%20Project%20Architecture.png)

---

## Implementation Steps

---

### 1. DynamoDB Table Created

Created a DynamoDB table to store order details.

**Why:**  
Acts as the **central state management system** for all orders.

![DynamoDB](Screenshots/01%20DynamoDB%20Table%20Created.png)

---

### 2. PlaceOrder Lambda Function Created

Created Lambda function to place new orders.

![PlaceOrder](Screenshots/02%20PlaceOrder%20Function%20Created.png)

---

### 3. PlaceOrder Code Implemented

Added logic to:
- Generate order ID  
- Store order in DynamoDB  
- Set initial status = PLACED  

![Code](Screenshots/03%20Code%20Updated%20in%20PlaceOrder%20Function.png)

---

### 4. IAM Policy Attached to Lambda

Attached required permissions for DynamoDB access.

**Why:**  
Ensures Lambda can interact with AWS services securely.

![IAM](Screenshots/04%20Adding%20Policy%20to%20Lambda%20Role.png)

---

### 5. PlaceOrder Function Tested

Triggered Lambda and verified successful execution.

![Test](Screenshots/05%20Testing%20Placeorder%20Function%20Code.png)

---

### 6. Data Stored in DynamoDB

Confirmed order entry in database.

![DB Output](Screenshots/06%20Successful%20Output%20in%20DynamoDB.png)

---

### 7. AcceptOrder Lambda Created

Handles order acceptance stage.

![Accept](Screenshots/07%20AcceptOrder%20Function%20Created.png)

---

### 8. AcceptOrder Logic Implemented

Updates order status → ACCEPTED

![Accept Code](Screenshots/08%20Code%20Updated%20in%20AcceptOrder%20Function.png)

---

### 9. PrepareOrder Lambda Created

Handles preparation stage.

![Prepare](Screenshots/09%20PrepareOrder%20Function%20Created.png)

---

### 10. PrepareOrder Logic Implemented

Updates order status → PREPARING

![Prepare Code](Screenshots/10%20Code%20Updated%20in%20PrepareOrder%20Function.png)

---

### 11. PrepareOrder Tested

Verified status update functionality.

![Prepare Test](Screenshots/11%20Testing%20PrepareOrder%20Function.png)

---

### 12. Updated Data Verified in DynamoDB

Confirmed status transition in database.

![DB Update](Screenshots/12%20Successful%20Output%20in%20DynamoDB.png)

---

### 13. DeliverOrder Lambda Created

Handles final delivery stage.

![Deliver](Screenshots/13%20DeliverOrder%20Function%20Created.png)

---

### 14. DeliverOrder Logic Implemented

- Updates status → DELIVERED  
- Generates receipt  
- Stores in S3  
- Sends notification  

![Deliver Code](Screenshots/14%20Code%20Updated%20in%20DeliverOrder%20Function.png)

---

### 15. Final Status Verified

Confirmed final state in DynamoDB.

![Final DB](Screenshots/15%20Successful%20Output%20in%20DynamoDB.png)

---

### 16. SNS Topic Created

Configured SNS for sending email notifications.

![SNS](Screenshots/16%20SNS%20Topic%20Created.png)

---

### 17. Receipt Stored in S3

Order receipt successfully saved in S3 bucket.

![S3](Screenshots/17%20Delivered%20Order%20Details%20Stored%20in%20S3.png)

---

### 18. EC2 Instance Created

Launched EC2 instance for simulation.

![EC2](Screenshots/18%20EC2%20Instance%20Created.png)

---

### 19. Multiple Orders Simulated from EC2

Used AWS CLI to trigger multiple orders.

![Simulation](Screenshots/19%20Creating%20Multiple%20Orders%20from%20EC2.png)

---

### 20. All Orders Verified in DynamoDB

Confirmed multiple orders processed successfully.

![Final Output](Screenshots/20%20All%20Orders%20Received%20in%20DynamoDB.png)

---

## 📊 Monitoring

Used CloudWatch for:
- Lambda execution logs  
- Error tracking  
- Debugging  

---

## 🧠 Key Features

✔ Serverless architecture using Lambda  
✔ State management using DynamoDB  
✔ Real-time notifications using SNS  
✔ Persistent storage using S3  
✔ Monitoring using CloudWatch  
✔ EC2-based simulation for real-world testing  
✔ Multi-step order lifecycle  

---

## 🎯 Learning Outcomes

- Built event-driven serverless architecture  
- Implemented multi-step workflow system  
- Integrated multiple AWS services  
- Understood IAM roles and permissions  
- Simulated real-world system behavior  
- Gained hands-on experience with AWS CLI  

---

## 🏁 Conclusion

This project demonstrates how to build a **scalable, event-driven backend system** using AWS serverless services. 
