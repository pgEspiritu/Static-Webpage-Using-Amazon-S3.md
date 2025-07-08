## 📸 Project Screenshots

Below are the screenshots documenting the full deployment process of hosting a static site (`faq.html`) using AWS S3 and CloudFront.  
All images are stored in the `images/` folder of this repository.

---

### 🪣 1. Creating an S3 Bucket
Setting up a new S3 bucket to host the static site.
![Creating S3 Bucket](images/Creating-S3-Bucket.png)

---

### 🔐 2. Configuring Bucket Policy
Applying a custom bucket policy to allow public access to the website files.
![Changing Bucket Policy](images/Changing-Bucket-Policy.png)

---

### 🌐 3. Enabling Static Website Hosting
Turning on static website hosting and specifying the index document (`faq.html`).
![Enabling Static Website Hosting](images/Enabling-Static-Website-Hosting.png)

---

### 📁 4. Uploading `faq.html` to S3
Uploading the main HTML file (`faq.html`) into the S3 bucket.
![Uploading faq.html](images/Uploading-faq.html-To-S3-Bucket.png)

---

### 🚀 5. CloudFront Setup – Step 1
Starting the process of creating a CloudFront distribution for the S3 site.
![CloudFront Step 1](images/Setting-CloudFront-S1.png)

---

### 🚀 6. CloudFront Setup – Step 2
Selecting the S3 website endpoint as the origin.
![CloudFront Step 2](images/Setting-CloudFront-S2.png)

---

### 🚀 7. CloudFront Setup – Step 3
Configuring cache behavior and viewer protocol policy.
![CloudFront Step 3](images/Setting-CloudFront-S3.png)

---

### 🚀 8. CloudFront Setup – Step 4
Finalizing the settings before creating the distribution.
![CloudFront Step 4](images/Setting-CloudFront-S4.png)

---

### ✅ 9. CloudFront Distribution Successfully Created
CloudFront distribution is now active and linked to the S3 bucket.
![CloudFront Created](images/CloudFront-Created.png)

---

### 🌍 10. Website Live via CloudFront
The `faq.html` page successfully loaded from CloudFront, confirming the site works globally.
![Working Website via CloudFront](images/Working-Static-Website-via-CloudFront-Origin.png)
