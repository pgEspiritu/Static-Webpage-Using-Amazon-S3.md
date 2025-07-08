# FAQs Stating Webpage Code (HTML) 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Help Center | FAQ</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
      background-color: #f9f9f9;
      color: #333;
    }
    h1 {
      color: #004080;
    }
    .faq {
      margin-top: 20px;
    }
    .faq-item {
      margin-bottom: 25px;
    }
    .question {
      font-weight: bold;
      font-size: 1.2em;
    }
    .answer {
      margin-top: 5px;
    }
    footer {
      margin-top: 50px;
      font-size: 12px;
      color: gray;
      text-align: center;
    }
  </style>
</head>
<body>

  <h1>Help Center – Frequently Asked Questions</h1>

  <div class="faq">

    <div class="faq-item">
      <div class="question">Q1: How can I reset my password?</div>
      <div class="answer">A: Navigate to <strong>Settings &gt; Security</strong> and click on <em>"Reset Password"</em>. Follow the prompts to complete the process.</div>
    </div>

    <div class="faq-item">
      <div class="question">Q2: How do I contact customer support?</div>
      <div class="answer">A: You can email us at <a href="mailto:support@example.com">support@example.com</a> or use the chat option in the lower-right corner of the screen.</div>
    </div>

    <div class="faq-item">
      <div class="question">Q3: Where can I find my billing history?</div>
      <div class="answer">A: Go to <strong>Account &gt; Billing</strong> to view and download your billing statements.</div>
    </div>

    <div class="faq-item">
      <div class="question">Q4: Can I change my subscription plan?</div>
      <div class="answer">A: Yes, visit the <strong>Subscription</strong> page under your account settings to upgrade, downgrade, or cancel your plan.</div>
    </div>

    <div class="faq-item">
      <div class="question">Q5: How do I report a bug or issue?</div>
      <div class="answer">A: Please report bugs via the <strong>Feedback</strong> option on your dashboard, or contact us directly at <a href="mailto:bugs@example.com">bugs@example.com</a>.</div>
    </div>

  </div>

  <footer>
    This site is hosted using <strong>AWS S3 + CloudFront</strong><br>
    &copy; 2025 Paolo Gio Espiritu - Cloud Engineer. All rights reserved.
  </footer>

</body>
</html>
```
