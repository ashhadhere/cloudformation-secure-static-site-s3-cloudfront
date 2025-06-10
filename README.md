# 🔒 Secure Static Website with S3 + CloudFront (OAC) – AWS CloudFormation

This CloudFormation template provisions a secure, scalable static website hosting solution using **Amazon S3** and **CloudFront**, with **Origin Access Control (OAC)**.

---

## ✅ Features

- Private S3 bucket (not publicly accessible)
- CloudFront as the only public access point
- Origin Access Control (OAC) for secure access
- HTTPS (redirect-to-https)
- Default root object: `index.html`
- Minimal and production-ready

---

## 🚀 Deployment

### Requirements

- AWS CLI configured
- Valid profile and region (e.g., `--profile infotech --region us-east-1`)
- A local folder with static site files (`index.html`, etc.)

### Deploy CloudFormation Stack

```bash
aws cloudformation deploy \
  --template-file template.yaml \
  --stack-name StaticSiteStack \
  --capabilities CAPABILITY_NAMED_IAM \
  --region us-east-1 \
  --profile infotech
```

---

## 📤 Upload Your Website Files

```bash
aws s3 sync ./site-content s3://<BucketName> \
  --acl bucket-owner-full-control \
  --profile infotech \
  --region us-east-1
```

> Replace `<BucketName>` with the name from the CloudFormation output.

---

## 🌍 Access Your Site

The CloudFront URL will be shown in the output, e.g.:

```
https://d1234abc.cloudfront.net
```

---

## 🔐 Security

- S3 bucket is fully private
- CloudFront accesses content using signed requests (OAC)
- Bucket policy only allows CloudFront (not public users)

---

## 📄 License

MIT License

---

## 🙋 Author

Built by **Ashhad Ali** – DevOps Engineer  
🔗 [LinkedIn](https://www.linkedin.com/in/ashhadali1)  
🌐 [https://www.ashhadali.com](https://www.ashhadali.com)
