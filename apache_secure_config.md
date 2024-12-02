# Apache HTTP Server Secure Configurations

## 1. Disable Directory Listing
Add the following to your `httpd.conf` or `apache2.conf` to prevent the directory listing:
```bash
Options -Indexes

## Use Secure HTTP Headers
Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"
Header always set X-Content-Type-Options "nosniff"
Header always set X-Frame-Options "SAMEORIGIN"
Header always set X-XSS-Protection "1; mode=block"
Header always set Content-Security-Policy "default-src 'self'"

## Disable SSLv2 and SSLv3
SSLProtocol all -SSLv2 -SSLv3

##Enable Strong Cipher Suites
#In your ssl.conf, add:
SSLCipherSuite HIGH:!aNULL:!MD5:!RC4

##Redirect HTTP to HTTPS
Add this to your .htaccess or apache2.conf:

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]


##Limit Allowed HTTP Methods
Disable methods like TRACE and TRACK:

<LimitExcept GET POST PUT DELETE OPTIONS>
    Deny from all
</LimitExcept>


