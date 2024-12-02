# Secure HTTP Headers

## 1. Strict-Transport-Security (HSTS)
This header forces browsers to communicate with your site over HTTPS only.
```bash
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload

##Content-Security-Policy (CSP)
This helps prevent XSS attacks by specifying which resources are allowed to be loaded.

Content-Security-Policy: default-src 'self'; script-src 'self' https://apis.google.com; object-src 'none'

##X-Content-Type-Options
This header prevents browsers from interpreting files as a different MIME type.


X-Content-Type-Options: nosniff

##X-Frame-Options
This header prevents your site from being embedded in an iframe, mitigating clickjacking.

X-Frame-Options: DENY

## X-XSS-Protection
This header enables the XSS filter built into most modern browsers.

X-XSS-Protection: 1; mode=block


Referrer-Policy
This header controls how much referrer information is sent with requests.

Referrer-Policy: no-referrer-when-downgrade





