You're still seeing:

```xml
<Error>
  <Code>AccessDenied</Code>
  <Message>Access Denied</Message>
</Error>
```

### 🔲 1. You're Using the Correct CloudFront Origin 
> (In this troubleshooting guide, the bucket name is `project-static-webpage`. Change the bucket name in your case.)

Go to: CloudFront > Your Distribution > Origins and Origin Groups

Origin Domain Name should be:
```text
project-static-webpage.s3-website-<region>.amazonaws.com
```

❗ Not:
```text
project-static-webpage.s3.amazonaws.com
```

#### ✅ Make sure:
- Origin type is automatically set to `Custom Origin`
- Origin protocol policy is set to `HTTP Only`

---

### 🔲 2. Bucket Policy Is Correct
Your policy looks fine, but just in case, here’s a verified working version:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::project-static-webpage/*"
    }
  ]
}
```
✅ If you have extra statements, keep them — but ensure this one exists.

---

### 🔲 3. Block Public Access Is Disabled
Path:
S3 → Your Bucket → Permissions → Block public access settings
> ✅ All four checkboxes must be unchecked. If any are checked, click Edit and disable them.

---

### 🔲 4. Object ACLs
✅ faq.html Set: has Everyone (public access) → `Read`

---

### 🔲 5. Test S3 Website Endpoint Directly
Paste this into your browser:
```bash
http://project-static-webpage.s3-website-<your-region>.amazonaws.com/faq.html
```
> ✅ If this works: Your S3 config is fine → the problem is likely in CloudFront origin.


### 🔲 6. CloudFront Cache
Even if you fixed everything, CloudFront might still serve an old cached error.
To invalidate the cache:
1. Go to your CloudFront distribution.
2. Click Invalidations → Create Invalidation
3. Enter:
   ```bash
   /faq.html
   ```
4. Click Invalidate
> This forces CloudFront to re-fetch the latest version.

---

### 🔲 7. (Last Resort) — Test Public Access Directly
Try accessing directly:
```bash
https://project-static-webpage.s3.amazonaws.com/faq.html
```

Or:
```
http://project-static-webpage.s3-website-<region>.amazonaws.com/faq.html
```

❌ If both fail, the issue is entirely within S3 permissions.

---

## ✅ Summary: Focus on These Top 3 Items
1. Use the correct CloudFront origin
(static website endpoint, not REST API)

2. Invalidate CloudFront cache
(ensure you're not seeing an outdated error)

3. Ensure S3 Block Public Access is fully disabled



