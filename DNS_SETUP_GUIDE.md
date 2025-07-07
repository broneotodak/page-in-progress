# DNS Configuration Guide for syaiton.com

## Quick Fix Instructions

Your site is live at: `syaiton.netlify.app` ✅
But not at: `www.syaiton.com` ❌

This means DNS is not configured properly.

## Step 1: Check Netlify Settings

1. Go to https://app.netlify.com
2. Select your site
3. Go to **Domain settings**
4. Add custom domain: `www.syaiton.com` and `syaiton.com`

## Step 2: Configure DNS at Your Domain Registrar

### If using GoDaddy:
1. Login to GoDaddy
2. Go to **My Products** → **Domains**
3. Click **DNS** next to syaiton.com
4. Delete existing A records
5. Add:
   - Type: A, Name: @, Value: 75.2.60.5
   - Type: CNAME, Name: www, Value: syaiton.netlify.app

### If using Namecheap:
1. Login to Namecheap
2. Go to **Domain List**
3. Click **Manage** next to syaiton.com
4. Go to **Advanced DNS**
5. Add:
   - Type: A Record, Host: @, Value: 75.2.60.5
   - Type: CNAME Record, Host: www, Value: syaiton.netlify.app

### If using Cloudflare:
1. Login to Cloudflare
2. Select syaiton.com
3. Go to **DNS**
4. Add:
   - Type: A, Name: @, Content: 75.2.60.5, Proxy: OFF
   - Type: CNAME, Name: www, Content: syaiton.netlify.app, Proxy: OFF

### If using another registrar:
Look for DNS Management, DNS Records, or Zone File settings

## Step 3: Wait for Propagation

- DNS changes take 5 minutes to 48 hours to propagate
- Check status at: https://www.whatsmydns.net
- Test your domain: http://www.syaiton.com

## Troubleshooting

### Still not working after 24 hours?

1. **Check SSL Certificate in Netlify:**
   - Domain settings → HTTPS → "Verify DNS configuration"
   - Click "Provision certificate"

2. **Clear DNS Cache:**
   - Windows: `ipconfig /flushdns`
   - Mac: `sudo dscacheutil -flushcache`
   - Chrome: chrome://net-internals/#dns → Clear host cache

3. **Verify Records:**
   - Use: https://dnschecker.org
   - Enter: syaiton.com
   - Check A and CNAME records

## Alternative: Use Netlify DNS (Easier)

Instead of adding records, change nameservers to:
- dns1.p04.nsone.net
- dns2.p04.nsone.net
- dns3.p04.nsone.net
- dns4.p04.nsone.net

This hands over DNS control to Netlify completely.

## Need More Help?

- Netlify Docs: https://docs.netlify.com/domains-https/custom-domains/
- Contact Netlify Support: https://www.netlify.com/support/

---

Your ASCII skull page will be live at www.syaiton.com once DNS is configured! 💀