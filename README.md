# Host a Static FAQ or Help Page Using Amazon S3 + CloudFront

# 🛠️ Deploy a Static FAQ Page on AWS (S3 + CloudFront)

## ✅ Step 1: Write Your FAQ Page

1. Open your editor (VS Code or Notepad)
2. Create and save this as `faq.html`: [**HTML Code**](FAQs-Webpage-HTML.md)

---

## ☁️ Step 2: Upload It to an S3 Bucket

### 1. Sign in to the AWS Console
- Visit: [https://console.aws.amazon.com/](https://console.aws.amazon.com/)
- Log in with your AWS account.

---

### 2. Navigate to S3
- In the search bar, type **S3**.
- Click on **S3** (Scalable Storage in the Cloud).

---

### 3. Create a New Bucket
- Click **Create bucket**.
- **Bucket name**: `your-help-page-bucket`  
  *(Must be globally unique. Rename if necessary.)*
- **Region**: Select your preferred AWS region.
- Scroll to **Block Public Access settings**:
  - ❗ **Uncheck**: "Block all public access"
  - Confirm by checking the acknowledgment box.
- Click **Create bucket**.

---

### 4. Upload Your `faq.html` File
- Click on your new bucket name.
- Click **Upload**.
- Click **Add files** and select `faq.html`.
- Click **Upload** at the bottom.

---

### 5. Enable Static Website Hosting
- Go to the **Properties** tab in your bucket.
- Scroll down to **Static website hosting**.
- Click **Edit**.
- ✅ **Enable static website hosting**
- **Index document**: `faq.html`
- Leave the **Error document** blank (optional).
- Click **Save changes**.

---

### 6. Get Your Website Link
- Still under **Static website hosting**, copy the **Bucket website endpoint** URL.
- This will be your temporary public website link.

Example: 

```html
http://your-help-page-bucket.s3-website-<region>.amazonaws.com
```

---

## 🔐 Step 3: Make the Bucket Public

1. In the AWS Console, go to your **S3 bucket** → **Permissions** tab.
2. Scroll to **Bucket Policy** and click **Edit**.
3. Paste the following JSON policy:

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [{
       "Sid": "PublicReadGetObject",
       "Effect": "Allow",
       "Principal": "*",
       "Action": "s3:GetObject",
       "Resource": "arn:aws:s3:::your-help-page-bucket/*"
     }]
   }
   ```
4. 🔁 Replace your-help-page-bucket with your actual bucket name.
5. Click Save to apply the policy.
