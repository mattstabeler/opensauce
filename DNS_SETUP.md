# DNS Setup Instructions for opensauce.stabeler.com

This document provides instructions for setting up the custom subdomain `opensauce.stabeler.com` to point to this GitHub Pages site.

## Overview

The site is configured to use the custom subdomain `opensauce.stabeler.com` instead of the default `mattstabeler.github.io/opensauce` URL.

## DNS Configuration with DNS Made Easy

DNS Made Easy is the DNS provider for the stabeler.com domain. Follow these steps to configure the subdomain:

### Steps to Configure DNS Made Easy

1. **Log in to DNS Made Easy**
   - Navigate to [https://dnsmadeeasy.com/](https://dnsmadeeasy.com/)
   - Log in with your DNS Made Easy account credentials

2. **Select the Domain**
   - From the dashboard, locate and click on `stabeler.com` from your managed domains list

3. **Add CNAME Record**
   - Click on the "A/AAAA Records" or "CNAME Records" section
   - Click "Add New Record" or the "+" button
   - Configure the following:
     - **Record Type**: CNAME
     - **Name**: `opensauce` (this creates opensauce.stabeler.com)
     - **Value/Target**: `mattstabeler.github.io`
     - **TTL**: 3600 (or leave as default)
   - Click "Submit" or "Save" to create the record

### Alternative: Using A Records

If you prefer to use A records instead of CNAME (for apex domain support), you can configure:

1. **Add A Records**
   - Record Type: A
   - Name: `opensauce`
   - Value: Add all four GitHub Pages IP addresses (create separate records for each):
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - TTL: 3600

2. **Add AAAA Records (IPv6)**
   - Record Type: AAAA
   - Name: `opensauce`
   - Value: Add all four IPv6 addresses (create separate records for each):
     - `2606:50c0:8000::153`
     - `2606:50c0:8001::153`
     - `2606:50c0:8002::153`
     - `2606:50c0:8003::153`
   - TTL: 3600

### DNS Propagation

- DNS changes typically propagate within 15 minutes to 24 hours
- You can check DNS propagation status using tools like:
  - [https://www.whatsmydns.net/](https://www.whatsmydns.net/)
  - Command line: `nslookup opensauce.stabeler.com` or `dig opensauce.stabeler.com`

## GitHub Pages Configuration

The repository is already configured for the custom domain. Here's what has been set up:

### 1. CNAME File

A `CNAME` file has been created in the repository root with the content:
```
opensauce.stabeler.com
```

This file tells GitHub Pages which custom domain to use.

### 2. Repository Configuration (_config.yml)

The `_config.yml` file has been updated with:
```yaml
url: "https://opensauce.stabeler.com"
baseurl: ""
```

This ensures Jekyll generates correct URLs for the custom domain.

### 3. GitHub Pages Settings (Manual Verification)

To verify or update the custom domain in GitHub's UI:

1. Go to the repository on GitHub: [https://github.com/mattstabeler/opensauce](https://github.com/mattstabeler/opensauce)
2. Click on "Settings" in the repository menu
3. Scroll down to the "GitHub Pages" section (or click "Pages" in the left sidebar)
4. In the "Custom domain" field, verify it shows: `opensauce.stabeler.com`
5. Ensure "Enforce HTTPS" is checked (GitHub will automatically provision an SSL certificate)

**Note**: GitHub Pages will automatically detect the CNAME file in the repository and apply the custom domain setting.

## HTTPS/SSL Certificate

GitHub Pages automatically provides free SSL certificates for custom domains using Let's Encrypt:

- After DNS propagates, GitHub will automatically provision an SSL certificate
- This process can take up to 24 hours after DNS is properly configured
- Once complete, the site will be accessible via `https://opensauce.stabeler.com`
- HTTP requests will automatically redirect to HTTPS

## Verification Steps

After completing the DNS and GitHub Pages setup:

1. **Wait for DNS Propagation** (15 minutes to 24 hours)
   
2. **Check DNS Resolution**
   ```bash
   nslookup opensauce.stabeler.com
   # Should return GitHub Pages IP addresses
   ```

3. **Test HTTP Access**
   ```bash
   curl -I http://opensauce.stabeler.com
   # Should redirect to HTTPS once SSL is provisioned
   ```

4. **Visit the Site**
   - Open a browser and navigate to `https://opensauce.stabeler.com`
   - The site should load with your recipes content

5. **Verify SSL Certificate**
   - Click the padlock icon in the browser address bar
   - Certificate should show as valid and issued by Let's Encrypt

## Troubleshooting

### DNS Not Resolving
- Verify the CNAME or A records are correctly configured in DNS Made Easy
- Check for typos in the subdomain name or target
- Wait longer for DNS propagation (up to 24 hours)

### Site Not Loading
- Ensure the CNAME file exists in the repository root
- Verify GitHub Pages is enabled in repository settings
- Check that the branch is set correctly (usually `master` or `main`)

### SSL Certificate Not Provisioning
- Ensure DNS is fully propagated first
- Disable and re-enable "Enforce HTTPS" in GitHub Pages settings
- Wait up to 24 hours for automatic certificate provisioning

### 404 Errors on Pages
- Verify the `baseurl` in `_config.yml` is set to `""` (empty string)
- Clear browser cache and try again
- Check that internal links don't include `/opensauce/` prefix

## Additional Resources

- [GitHub Pages Custom Domain Documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [DNS Made Easy Support](https://dnsmadeeasy.com/support/)
- [GitHub Pages IP Addresses](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)

## Support

For DNS issues, contact DNS Made Easy support or your domain administrator.

For GitHub Pages issues, refer to [GitHub's documentation](https://docs.github.com/en/pages) or [contact GitHub support](https://support.github.com/).
