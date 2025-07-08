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


---

## 🚀 Step 4: Add CloudFront for Global Speed

Amazon CloudFront is a **Content Delivery Network (CDN)** that speeds up your site by distributing your content to edge locations around the world. This means your `faq.html` will load faster for users no matter where they are.

---

#### 1. Go to the CloudFront Console
- In the AWS Console, search for **CloudFront** in the search bar.
- Click **CloudFront** to open the service.
- Click the **Create Distribution** button.

---

#### 2. Configure the Origin Settings
- Under **Origin domain**, click the dropdown and **paste your S3 static website endpoint URL**.  
  Example:  
 ```html
  http://your-help-page-bucket.s3-website-us-east-1.amazonaws.com
 ```

> ⚠️ **Important:** Do **not** use the default S3 bucket ARN shown in the list (e.g., `your-help-page-bucket.s3.amazonaws.com`)
> Instead, use the **static website endpoint** that looks like `http://...s3-website-...`.
> If error occurs, direct connect the s3 by clicking `browse S31, then find the S3 Bucket where the faq.html stored

- Keep **Origin path** blank.

- Leave **Origin access control settings** as default (no OAC/OAI needed for public static hosting).

---

#### 3. Default Cache Behavior Settings
- Leave most default options as is.
- **Viewer Protocol Policy**: Change to **Redirect HTTP to HTTPS** (optional, for secure access).
- **Allowed HTTP Methods**: Leave as **GET, HEAD**.
- **Caching**: Leave default unless you want custom caching rules.

---

#### 4. Distribution Settings
- **Price class**: You may choose **Use only U.S., Canada and Europe** for lower cost or **Use all edge locations** for maximum reach.
- **Alternate domain name (CNAME)**: Leave blank for now unless you plan to use a custom domain.
- **Custom SSL certificate**: Leave as **Default CloudFront certificate** for now (you'll get an HTTPS CloudFront URL).

- Click **Create Distribution**.

---

#### 5. Wait for Deployment
- You’ll see your new distribution listed.
- **Status** will show as “In Progress” – wait a few minutes for it to deploy.
- Once **Status** becomes “Deployed”, copy the **CloudFront Domain Name**.  
Example:
  ```html
  https://d1234abc.cloudfront.net
  ```

---

### ✅ You now have a CDN-accelerated, HTTPS-secured website link:
Open your CloudFront URL in a browser, and it will serve your `faq.html` from S3 via CloudFront.

---

### 🌟 Benefits of Using CloudFront
- ✅ **Faster Load Times** globally due to edge caching.
- ✅ **HTTPS Support** out-of-the-box.
- ✅ **Scalable and Reliable** — handles high traffic efficiently.
- ✅ **Cleaner Public URL** for sharing (vs. long S3 URLs).

---


