# Project 1 — Secure Static Website on AWS

## Objective
Deploy a static website using Amazon S3 with basic security controls.


## Architecture
The website is hosted using Amazon S3 static website hosting.  
Users access the site directly over the internet, and S3 serves the static content publicly based on the configured bucket policy.

**Flow:**
User → Internet → Amazon S3 (Static Website Endpoint)

## Steps
1. Create S3 bucket
2. Upload website files
3. Enable static website hosting
4. Apply bucket policy
5. Test public access

## Security Considerations
- Public access limited to website objects
- No credentials exposed

## Learning Outcomes
- Learned how S3 static website hosting differs from normal object access
- Understood how bucket policies control public access securely
- Practiced safe cloud experimentation using sandbox environments
- Gained experience documenting infrastructure changes clearly

## Why This Project Matters
Static websites are a common real-world use case for low-cost hosting, landing pages, documentation sites, and internal tools.  
This project demonstrates foundational cloud skills such as storage configuration, access control, and operational documentation.
  

