# Host a Static FAQ or Help Page Using Amazon S3 + CloudFront

# 🛠️ Deploy a Static FAQ Page on AWS (S3 + CloudFront)

## ✅ Step 1: Write Your FAQ Page

1. Open your editor (VS Code or Notepad)
2. Create and save this as `faq.html`: [**HTML Code**](FAQs-Webpage-HTML.md)

---

## ☁️ Step 2: Upload It to an S3 Bucket

1. Go to the **AWS Console** → **S3** → click **Create bucket**
2. Configure the bucket:
   - **Bucket name**: `your-help-page-bucket`
   - **Region**: Choose your preferred AWS region
   - ❗ **Uncheck**: “Block all public access”
3. Click **Create bucket**
4. Open the new bucket and click **Upload**
   - Upload your `faq.html` file
5. Go to **Properties** → scroll to **Static website hosting**
   - ✅ **Enable static website hosting**
   - **Index document**: `faq.html`
6. Click **Save changes**
7. Copy the **S3 website endpoint URL** — this will be your temporary site link.
