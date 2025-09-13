# EmailJS Setup Instructions for Contact Form

## Step 1: Create EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

## Step 2: Add Email Service

1. In EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose your email provider (Gmail recommended):
   - Select "Gmail"
   - Click "Connect Account"
   - Sign in with your Gmail account (`rozi.unix@gmail.com`)
   - Authorize EmailJS
4. Give your service a name (e.g., "GoGreens Contact")
5. Copy the **Service ID** (you'll need this later)

## Step 3: Create Email Template

1. Go to "Email Templates" in EmailJS dashboard
2. Click "Create New Template"
3. Use this template content:

**Subject:** New Contact Form Submission from {{from_name}}

**Body:**
```
You have received a new message from your website contact form.

From: {{from_name}}
Email: {{from_email}}
Company: {{company}}
Phone: {{phone}}

Message:
{{message}}

---
This message was sent from your GoGreens website contact form.
```

4. Save the template and copy the **Template ID**

## Step 4: Get Public Key

1. Go to "Account" → "General"
2. Copy your **Public Key**

## Step 5: Update Website Code

Open `site45-contact.html` and replace these placeholders:

1. **Line ~170**: Replace `YOUR_PUBLIC_KEY` with your actual public key
2. **Line ~207**: Replace `YOUR_SERVICE_ID` with your service ID  
3. **Line ~207**: Replace `YOUR_TEMPLATE_ID` with your template ID

Example:
```javascript
// Replace this:
publicKey: "YOUR_PUBLIC_KEY",

// With your actual key:
publicKey: "user_abc123xyz",

// Replace this:
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', formData)

// With your actual IDs:
emailjs.send('service_abc123', 'template_xyz789', formData)
```

## Step 6: Test the Form

1. Open `site45-contact.html` in your browser
2. Fill out the contact form
3. Submit the form
4. Check your email (`rozi.unix@gmail.com`) for the message
5. You should see a success message on the website

## Troubleshooting

- **Form not working?** Check browser console for errors (F12)
- **No email received?** Check spam folder and verify your email service setup
- **Error messages?** Make sure all IDs are correctly replaced in the code

## EmailJS Free Plan Limits

- 200 emails per month
- EmailJS branding in emails
- Perfect for small business contact forms

## Alternative: Formspree (Backup Option)

If EmailJS doesn't work, you can also use Formspree:

1. Go to [https://formspree.io/](https://formspree.io/)
2. Sign up for free account
3. Create a new form
4. Use the provided endpoint URL
5. Update the form action attribute

This setup will allow your contact form to send real emails to `rozi.unix@gmail.com` without needing a backend server!