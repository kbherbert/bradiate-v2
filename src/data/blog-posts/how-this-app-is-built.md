---
title: How this app is built
publishDate: 4 Nov 2024
description: Building My Blog with Astro and Infrastructure as Code
---

I built this blog using [Astro](https://astro.build/), a modern static site generator that makes it easy to create fast, content-focused websites. Astro's island architecture keeps JavaScript to a minimum while still allowing interactive components when needed, which is exactly what I wanted in order to achieve lighting-fast load times in Lighthouse.

The static output is hosted on [DigitalOcean](https://www.digitalocean.com/) using their static site App Platform, which automatically deploys from my GitHub repository. Every push triggers a new build and deployment—no manual steps required.

## Managing infrastructure as code

Rather than clicking through dashboards, I manage my DNS records using [HCP Terraform Cloud](https://cloud.hashicorp.com/products/terraform) with the [Cloudflare provider](https://registry.terraform.io/providers/cloudflare/cloudflare/latest/docs). This keeps my CNAME records, SSL certificates, and other DNS configuration versioned and reproducible. Any infrastructure change is tracked in git, reviewed as code, and deployed consistently.

The combination of Astro's simplicity, DigitalOcean's reliability, and Terraform's infrastructure-as-code approach gives me a blog setup that's fast, maintainable, and fully under version control.