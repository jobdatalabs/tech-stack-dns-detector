# Tech Stack & DNS Detector — website technologies + email provider + SaaS tools

[![Run on Apify](https://img.shields.io/badge/Run%20on-Apify-00a76f?style=for-the-badge)](https://apify.com/jobdata_labs/tech-stack-dns-detector)

> **Hosted version:** run it in the cloud, no install, pay per result: **[Tech Stack & DNS Detector: Website Tech, Email Provider, SaaS](https://apify.com/jobdata_labs/tech-stack-dns-detector)**

Find out **what a company runs on** from just its domain: website technologies **and** the business tools that only show up in **public DNS records** — email provider (Google Workspace, Microsoft 365…), email/marketing senders (HubSpot, Salesforce, Mailchimp, SendGrid…) and verified SaaS accounts (Atlassian, Slack, DocuSign, Zoom, OpenAI, Miro…).

Most tech detectors only read the HTML of a page. For B2B prospecting, knowing that a company **uses Microsoft 365 and HubSpot and has an Atlassian account** is often worth more than knowing it uses jQuery. This Actor gives you both in one row.

## What it detects

**From the homepage** (one request per domain, robots.txt respected): CMS & website builders (WordPress, Shopify, Webflow, Wix, Framer, Drupal…), JavaScript frameworks (Next.js, Nuxt, React, Vue, Angular…), analytics & tag managers, ad pixels (Meta, LinkedIn, TikTok, Google Ads…), marketing automation, live chat & support, payments, cookie consent, CDN & hosting (Cloudflare, Vercel, Netlify, CloudFront…), monitoring, A/B testing and more — ~120 rules.

**From public DNS:** email provider and email security gateway (MX), email sending services (SPF), verified SaaS (TXT verification records), DMARC policy, DNS provider (NS).

## Output example

```json
{
  "domain": "bunq.com",
  "emailProvider": "Google Workspace",
  "emailSendingServices": ["Mailchimp", "Salesforce", "Mandrill", "Google Workspace"],
  "verifiedServices": ["Apple", "DocuSign", "Miro", "Postman", "Microsoft 365"],
  "dnsProvider": "AWS Route 53",
  "dmarcPolicy": "reject",
  "technologies": [
    { "name": "Framer", "category": "Website builder", "evidence": "html" },
    { "name": "Sentry", "category": "Monitoring", "evidence": "html" }
  ],
  "allTechnologies": ["Google Workspace", "Mailchimp", "Salesforce", "DocuSign", "Miro", "Framer", "Sentry"],
  "technologyCount": 13
}
```

## Use cases

- **Lead generation & segmentation:** find companies on Microsoft 365 vs Google Workspace, on HubSpot vs Salesforce, on Shopify vs WooCommerce.
- **Competitive intelligence:** see which tools competitors and prospects adopt.
- **Sales personalization:** mention the stack the prospect already uses.
- **Email deliverability audits:** check SPF and DMARC policy across many domains.

## Pricing

Pay per event: **one fee per domain analyzed**. Domains that don't exist are not charged.

## Notes & limits

- Detection is signature-based: a technology loaded only after login or user interaction may not be visible.
- Sites that block automated access or disallow crawling in robots.txt are not fetched; DNS results are still returned.
- No personal data is collected.

---

## Run it via API

```bash
curl -X POST "https://api.apify.com/v2/acts/jobdata_labs~tech-stack-dns-detector/run-sync-get-dataset-items" \
  -H "Authorization: Bearer $APIFY_TOKEN" -H "Content-Type: application/json" \
  -d '{"helloWorld": 123}'
```

```js
import { ApifyClient } from 'apify-client';
const client = new ApifyClient({ token: process.env.APIFY_TOKEN });
const run = await client.actor('jobdata_labs/tech-stack-dns-detector').call({
    "helloWorld": 123
});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
```

## Use it from AI agents (MCP)

```json
{
  "mcpServers": {
    "tech-stack-dns-detector": {
      "url": "https://mcp.apify.com?tools=jobdata_labs/tech-stack-dns-detector",
      "headers": { "Authorization": "Bearer <YOUR_APIFY_TOKEN>" }
    }
  }
}
```

## More tools by jobdata_labs

All tools: [apify.com/jobdata_labs](https://apify.com/jobdata_labs) · [SEO Audit Crawler](https://apify.com/jobdata_labs/seo-audit-crawler) · [Sitemap Change Monitor](https://apify.com/jobdata_labs/sitemap-change-monitor) · [RSS Feed Monitor](https://apify.com/jobdata_labs/rss-feed-monitor) · [Tech Stack & DNS Detector](https://apify.com/jobdata_labs/tech-stack-dns-detector)
