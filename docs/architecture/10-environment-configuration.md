## Environment Configuration

```bash
# .env.local - Local development environment
NEXT_PUBLIC_WIX_API_URL=https://your-wix-site.wixsite.com/_functions
WIX_API_TOKEN=your_wix_api_token

# EmailJS Configuration
NEXT_PUBLIC_EMAILJS_SERVICE_ID=your_emailjs_service_id
NEXT_PUBLIC_EMAILJS_TEMPLATE_ID=your_emailjs_template_id
NEXT_PUBLIC_EMAILJS_PUBLIC_KEY=your_emailjs_public_key

# Namecheap Private Email
CONTACT_EMAIL=contact@agroventia.com
ADMIN_EMAIL=admin@agroventia.com

# Analytics (optional)
NEXT_PUBLIC_GA_MEASUREMENT_ID=G-XXXXXXXXXX

# Development
NODE_ENV=development
NEXT_PUBLIC_SITE_URL=http://localhost:3000

# .env.production - Production environment
NODE_ENV=production
NEXT_PUBLIC_SITE_URL=https://agroventia.com
```