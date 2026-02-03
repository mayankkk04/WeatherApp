# 🌦️ Cloud Hosted Weather App (AWS S3 + CloudFront)

A real-time Weather Application built with React and deployed on AWS Cloud using S3 Static Website Hosting and CloudFront CDN for secure and fast global delivery.

## 🚀 Project Overview

This project demonstrates how a React application can be deployed to AWS without using any traditional servers.

The app fetches real-time weather data from a public Weather API and is hosted using a serverless cloud architecture.

User → CloudFront (CDN + HTTPS) → S3 (Static Website Hosting) → Weather API
  
☁️ AWS Services Used
  
Amazon Web Services S3 — Static website hosting
  
Amazon CloudFront — CDN for fast global access + HTTPS

  
IAM & Bucket Policies — Secure public access

  
## Technologies Used

- **HTML**: For the basic structure of the app
- **CSS**: For styling and responsive design
- **JavaScript**: For interactive elements and handling API requests
- **React**: For building a component-based, dynamic user interface
- **OpenWeatherMap API**: For fetching weather data

  
3️⃣ Add Bucket Policy for Public Access
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::weather-app-mayank/*"
    }
  ]
}

  
4️⃣ Configure CloudFront

Origin: S3 static website endpoint

Viewer Protocol: Redirect HTTP → HTTPS

Default root object: index.html
## Getting Started

## 💡 Why this project is useful

  
This project shows how a frontend application can be deployed using cloud-native services without managing any servers, which is a common real-world architecture for static web apps.

  
🧠 Future Improvements
  
Add custom domain using Route 53


Add CI/CD using GitHub Actions

  
Add monitoring using CloudWatch

  
FontAwesome for weather icons
