# 🌦️ Cloud Hosted Weather App (AWS S3 + CloudFront)

A real-time Weather Application built with React and deployed on AWS Cloud using S3 Static Website Hosting and CloudFront CDN for secure and fast global delivery.

The site is live at CloudFornt - https://d3d285o9qolcni.cloudfront.net/
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

  
🧩 Part 1 — Prepare React App for S3 (Very Important)

S3 cannot run React source code. It only serves static files.

1. Open terminal in project folder
npm install
npm run build
2. This creates a folder:
build/
   index.html
   static/

These are the only files S3 needs.

🪣 Part 2 — Create S3 Bucket
Step 1

Go to: AWS Console → S3 → Create bucket

Step 2 — Bucket configuration
Setting	Value
Bucket name	weather-app-mayank
Region	Default
Block Public Access	❌ Uncheck “Block all public access”

Acknowledge warning → Create bucket

🌐 Part 3 — Enable Static Website Hosting
Step 1

Open bucket → Properties tab

Step 2

Scroll to Static website hosting → Edit

Setting	Value
Enable	✅
Index document	index.html

Save.

You will see:

weather-app-mayank.s3-website-us-east-1.amazonaws.com

⚠️ This is very important. Save this.

⬆️ Part 4 — Upload Build Files to S3
Step 1

Delete any existing files in bucket.

Step 2

Open local build/ folder.

Step 3

Go inside build folder and select:

index.html
static/

Upload these to S3.

Bucket root must look like:

index.html
static/
🔓 Part 5 — Add Bucket Policy (Critical Step)

Now your app works via:

http://weather-app-mayank.s3-website-us-east-1.amazonaws.com
☁️ Part 6 — Create CloudFront Distribution (for HTTPS J)

Go to: CloudFront → Create Distribution

Step 1 — Get started
Setting	Value
Distribution name	weather-app-mayank
Type	Single website or app

Next.

Step 2 — Specify Origin (MOST IMPORTANT)
Setting	Value
Origin type	Other
Origin domain	weather-app-mayank.s3-website-us-east-1.amazonaws.com
Origin protocol policy	HTTP only

Next.

Step 3 — Enable security
Setting	Value
Viewer protocol policy	Redirect HTTP to HTTPS

Next.

Step 4 — TLS certificate
Setting	Value
Certificate	Default CloudFront certificate

Next.

Step 5 — Review and create (VERY IMPORTANT)

Set:

Default root object = index.html
  
Create distribution.
  
Wait ~10 minutes until status = Deployed.
  
🔗 Part 7 — Get CloudFront URL
  
Go to:
  
CloudFront → Distributions → Open your distribution
  
Copy:
  
https://d32850qclnx.cloudfront.net
  
This is your final HTTPS app.
  
<pre>
✅ Final Architecture
User
  ↓
CloudFront (HTTPS)
  ↓
S3 Static Website Hosting
  ↓
Weather API
</pre>
🧠 Key Realizations During Setup
  
React source code cannot be hosted directly
   
S3 needs only build output
  
Bucket policy is required (ACL won’t work)
  
CloudFront needs S3 website endpoint, not bucket name

  
Default root object must be set to index.html


## Getting Started

## 💡 Why this project is useful

  
This project shows how a frontend application can be deployed using cloud-native services without managing any servers, which is a common real-world architecture for static web apps.

  
🧠 Future Improvements
  
Add custom domain using Route 53


Add CI/CD using GitHub Actions

  
Add monitoring using CloudWatch

  
FontAwesome for weather icons
