# IntoDNS - DNS & Email Security Analysis for your Terminal

**Stop switching to your browser.** Run a full DNS health check and email security audit from your terminal in seconds. Get a score, spot misconfigurations, and get copy-paste fixes - right where you work.

```
/intodns myproject.com
```

## Install

```bash
clawdhub install intodns
```

## Why developers use this

You just deployed a new project. Email isn't arriving. Is it SPF? DKIM? Did someone forget DMARC? Maybe DNSSEC broke after a migration?

IntoDNS gives you the answer in one command:

- **0-100 health score** so you know where you stand instantly
- **Pass/fail per category** - DNS, DNSSEC, SPF, DKIM, DMARC, MTA-STS, BIMI, blacklists
- **Concrete fixes** - not just "something is wrong" but exactly what to add or change
- **No signup, no API key** - just works

## What it checks

| Check | What you learn |
|-------|---------------|
| DNS Records | Are your A, AAAA, MX, NS, CAA records correct? |
| DNSSEC | Is your domain cryptographically signed? |
| SPF | Can spammers send email as you? |
| DKIM | Are your emails authenticated? |
| DMARC | What happens to failed authentication? |
| MTA-STS | Is email transport encrypted? |
| BIMI | Does your brand logo show in inboxes? |
| Blacklists | Are your mail server IPs flagged? |
| Propagation | Are your DNS changes live worldwide? |

## Example prompts

```
/intodns cobytes.com
```

```
Check if email is properly configured for mysite.nl
```

```
Does example.org have DNSSEC?
```

```
Full DNS security audit of mydomain.com
```

```
Why isn't email arriving for newproject.io?
```

## Example output

```
DNS Health Report: example.com

Score: 72/100

| Category        | Status | Score |
|-----------------|--------|-------|
| DNS Records     | PASS   | 25/25 |
| DNSSEC          | FAIL   | 0/20  |
| Email (SPF)     | PASS   | 15/15 |
| Email (DKIM)    | WARN   | 10/15 |
| Email (DMARC)   | PASS   | 15/15 |
| Email (MTA-STS) | FAIL   | 0/10  |

Issues:
- CRITICAL: DNSSEC not enabled
- WARNING: DKIM - only default selector found
- INFO: MTA-STS not configured

Full report: https://intodns.ai/scan/example.com
```

## Add a badge to your README

Show your domain's DNS health score:

```markdown
[![DNS Score](https://intodns.ai/api/badge/yourdomain.com)](https://intodns.ai/scan/yourdomain.com)
```

## API

Public API. No key required. No rate limit for normal usage.

| Endpoint | Description |
|----------|-------------|
| `/api/scan/quick?domain=X` | Full scan with score |
| `/api/dns/lookup?domain=X` | All DNS records |
| `/api/dns/dnssec?domain=X` | DNSSEC validation |
| `/api/email/check?domain=X` | Full email security |
| `/api/email/spf?domain=X` | SPF check |
| `/api/email/dkim?domain=X` | DKIM discovery |
| `/api/email/dmarc?domain=X` | DMARC check |
| `/api/email/mta-sts?domain=X` | MTA-STS check |
| `/api/email/bimi?domain=X` | BIMI check |
| `/api/email/blacklist?domain=X` | IP blacklist check |
| `/api/badge/DOMAIN` | SVG score badge |

Base URL: `https://intodns.ai`

Full API docs: [intodns.ai/developers](https://intodns.ai/developers)

---

Built by [Cobytes](https://cobytes.com) - Cybersecurity made simple.
