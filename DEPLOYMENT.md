# ClawdMate Deployment Guide

## Prerequisites Setup (Do This First!)

### 1. Google Workspace Setup
1. Go to https://workspace.google.com
2. Click "Get Started" 
3. Choose "For my business"
4. Enter business name: **ClawdMate**
5. Number of employees: **Just you**
6. Country: **[Your Country]**
7. Enter your personal email for account setup
8. Create first user: **ops@clawdmate.com**
9. Add your domain: **clawdmate.com**

### 2. Google Will Give You DNS Records

You'll receive something like:

**TXT Record (for verification):**
```
Name: @
Type: TXT
Value: google-site-verification=xxxxxxxxxxxxx
TTL: 1 hour
```

**MX Records (for email):**
```
Priority 1: ASPMX.L.GOOGLE.COM
Priority 5: ALT1.ASPMX.L.GOOGLE.COM
Priority 5: ALT2.ASPMX.L.GOOGLE.COM
Priority 10: ALT3.ASPMX.L.GOOGLE.COM
Priority 10: ALT4.ASPMX.L.GOOGLE.COM
```

### 3. Add DNS Records to GoDaddy

1. Log into GoDaddy
2. Go to "My Products"
3. Find clawdmate.com → Click "DNS"
4. Add the TXT record from Google
5. Add all 5 MX records from Google
6. Wait 10-15 minutes for DNS propagation

### 4. Verify Domain in Google Workspace

1. Go back to Google Workspace admin
2. Click "Verify domain"
3. It should detect the TXT record
4. Once verified, email will start working in 24-48 hours (usually faster)

---

## Deploy Website to Vercel

### Option A: Via GitHub (Recommended)

1. **Create GitHub Repo:**
   ```bash
   # In your terminal, navigate to the project folder
   cd clawdmate-web
   git init
   git add .
   git commit -m "Initial commit - ClawdMate landing page"
   ```

2. **Push to GitHub:**
   - Go to github.com
   - Create new repository: `clawdmate-web`
   - Keep it public or private (your choice)
   - Don't initialize with README (we have one)
   - Copy the commands GitHub gives you:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/clawdmate-web.git
   git branch -M main
   git push -u origin main
   ```

3. **Connect to Vercel:**
   - Go to vercel.com
   - Click "New Project"
   - Import your GitHub repo
   - Click "Deploy"
   - Done! Vercel gives you a URL like `clawdmate-web.vercel.app`

4. **Add Custom Domain:**
   - In Vercel project settings
   - Go to "Domains"
   - Add `clawdmate.com` and `www.clawdmate.com`
   - Vercel will give you DNS records

5. **Update GoDaddy DNS (Again):**
   - Add Vercel's A record or CNAME
   - Point `@` (root) to Vercel
   - Point `www` to Vercel
   - Wait 10-15 minutes

### Option B: Vercel CLI (Faster)

```bash
# Install Vercel CLI
npm i -g vercel

# Navigate to project
cd clawdmate-web

# Deploy
vercel

# Follow prompts:
# - Link to existing project? N
# - What's your project name? clawdmate-web
# - In which directory is your code located? ./
# - Want to override settings? N

# Add custom domain
vercel domains add clawdmate.com
```

---

## Post-Deployment Checklist

- [ ] Google Workspace set up
- [ ] ops@clawdmate.com email working (test by sending yourself an email)
- [ ] Website live at clawdmate.com
- [ ] Both Google and Outlook sign-in buttons visible
- [ ] Mobile responsive (test on phone)
- [ ] SSL/HTTPS working (should be automatic)

---

## Next Steps

Once email and website are live:

1. **Create API Accounts** (use ops@clawdmate.com):
   - DeepSeek/Kimi API
   - Google Cloud Console (for Gmail/Calendar APIs)
   - Telegram Bot

2. **Build the Bot:**
   - Set up Telegram bot backend
   - Connect to Gmail/Calendar
   - Integrate Kimi K2.5

3. **Test with yourself:**
   - Connect your personal Gmail
   - Test all commands
   - Iterate and improve

---

## Support

Questions? Email ops@clawdmate.com (once it's working!) 😄

Or revisit this chat for help.
