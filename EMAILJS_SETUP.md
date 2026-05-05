# EmailJS Setup Guide

This guide will help you get your contact form sending emails.

## Steps to Configure EmailJS

### 1. Create an EmailJS Account
- Go to [emailjs.com](https://www.emailjs.com/)
- Sign up for a free account
- Verify your email

### 2. Get Your Public Key
- Log in to your EmailJS dashboard
- Go to **Account** → **API Keys**
- Copy your **Public Key**
- Replace `YOUR_PUBLIC_KEY_HERE` in `index.html` with this key

### 3. Create an Email Service
- In the dashboard, go to **Email Services**
- Click **Create New Service**
- Choose your email provider (Gmail, Outlook, etc.)
- Follow the authentication steps
- Name it something like "Contact Form Service"
- Once created, copy your **Service ID**
- Replace `SERVICE_ID_HERE` in `index.html` with this ID

### 4. Create an Email Template
- In the dashboard, go to **Email Templates**
- Click **Create New Template**
- Set the template name (e.g., "Contact Form")
- In the template editor, use these template variables:

```
From: {{email}}
Name: {{name}}
Type: {{type}}
Subject: {{subject}}

Message:
{{message}}
```

Configure the email:
- **To Email**: Your email address (or use `{{to_email}}` if you want it dynamic)
- **Subject**: `New Contact Form Submission: {{subject}}`
- **Content**: Use the variables above

- Once created, copy your **Template ID**
- Replace `TEMPLATE_ID_HERE` in `index.html` with this ID

### 5. Update Your HTML File

Find these three lines in `index.html` and replace them:

```javascript
emailjs.init({
  publicKey: 'YOUR_PUBLIC_KEY_HERE', // ← Replace this
});

await emailjs.sendForm(
  'SERVICE_ID_HERE',        // ← Replace this
  'TEMPLATE_ID_HERE',       // ← Replace this
  contactForm
);
```

### 6. Test Your Contact Form

- Open your website in a browser
- Fill out the contact form
- Click "Send Message"
- You should receive an email!

## Form Fields Available

The following form fields are automatically sent with each submission:
- `name` - Full Name
- `email` - Email Address
- `subject` - Subject line
- `type` - Inquiry Type (dropdown)
- `message` - Message content

## Troubleshooting

### "Invalid credentials" error
- Double-check that your Public Key, Service ID, and Template ID are correct
- Make sure there are no extra spaces

### Emails not arriving
- Check your EmailJS dashboard for failed sends
- Verify your email service is properly connected
- Check spam/junk folders

### Form button not responding
- Open browser console (F12) to check for JavaScript errors
- Make sure the EmailJS library loaded correctly
- Verify all three credentials are set

## Free Tier Limits

EmailJS free tier allows:
- Up to 200 emails per month
- Email services from various providers
- Perfect for a contact form!

If you need more, upgrade to a paid plan.
