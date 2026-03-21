# IntoDNS - DNS & Email Security Analysis

**Comprehensive domain security scanning from your terminal.** Run 50+ DNS and email security checks in under 3 seconds. Get a score, spot misconfigurations, and get copy-paste fixes - right where you work.

```
/intodns myproject.com
```

[![npm](https://img.shields.io/npm/v/intodns)](https://www.npmjs.com/package/intodns)

## Install

```bash
clawhub install intodns
```

## What it checks

| Category | Checks | Weight |
|----------|--------|--------|
| DNS Records | A, AAAA, MX, NS, SOA, CAA, CNAME | 20% |
| DNSSEC | Chain validation, DS records, algorithm checks | 15% |
| Email - SPF | Record parsing, DNS lookup counting (RFC 7208) | 30% |
| Email - DKIM | Selector discovery across 20+ common selectors | |
| Email - DMARC | Policy analysis, alignment checks | |
| Email - MTA-STS | Policy file validation, transport encryption | |
| Email - BIMI | Brand logo validation (SVG Tiny 1.2 PS) | |
| IPv6 | AAAA records, dual-stack readiness | 15% |
| Security | IP blacklist checks (6+ lists), best practices | 20% |

Grades: A+ (100%), A (90-99%), B (80-89%), C (70-79%), D (50-69%), F (0-49%)

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

```
Is my domain blacklisted?
```

```
Generate a PDF report for example.com
```

## Example output

```
DNS Health Report: cobytes.com

Grade: A+ | Score: 100/100

| Category          | Status | Score |
|-------------------|--------|-------|
| DNS Records       | PASS   | 100%  |
| DNSSEC            | PASS   | 100%  |
| Email Security    | PASS   | 100%  |
| IPv6              | PASS   | 100%  |
| Security          | PASS   | 100%  |

No issues found.

Full report: https://intodns.ai/scan/cobytes.com
```

## Also available as

### npm CLI

```bash
npx intodns example.com
npx intodns example.com --json
npx intodns example.com --fail-below 80
```

### GitHub Action

```yaml
- name: DNS Security Check
  uses: RoscoNL/dns-security-scanner/github-action@main
  with:
    domain: example.com
    fail-below: 70
```

### PDF Reports

Download a full PDF security report:

```
https://intodns.ai/api/pdf/yourdomain.com
```

### Score Badge

Add a DNS health badge to your README:

```markdown
[![DNS Score](https://intodns.ai/api/badge/yourdomain.com)](https://intodns.ai/scan/yourdomain.com)
```

## API

Public API. No key required. No signup.

| Endpoint | Description |
|----------|-------------|
| `/api/scan/quick?domain=X` | Full scan with score, grade, categories |
| `/api/dns/lookup?domain=X` | All DNS records |
| `/api/dns/lookup?domain=X&type=MX` | DNS records by type |
| `/api/dns/dnssec?domain=X` | DNSSEC validation |
| `/api/dns/propagation?domain=X` | Worldwide DNS propagation |
| `/api/email/check?domain=X` | Full email security |
| `/api/email/spf?domain=X` | SPF check |
| `/api/email/dkim?domain=X` | DKIM discovery |
| `/api/email/dmarc?domain=X` | DMARC check |
| `/api/email/mta-sts?domain=X` | MTA-STS check |
| `/api/email/bimi?domain=X` | BIMI check |
| `/api/email/blacklist?domain=X` | IP blacklist check |
| `/api/badge/DOMAIN` | SVG score badge |
| `/api/pdf/DOMAIN` | PDF security report |

Base URL: `https://intodns.ai`

---

Built by [Cobytes](https://cobytes.com) - Cybersecurity made simple.
