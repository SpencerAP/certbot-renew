# certbot-renew
A bash script I use to automate renewing my Let’s Encrypt SSL certificates.

## Background
[Let's Encrypt](https://letsencrypt.org/ "Let's Encrypt") and its companion [certbot](https://certbot.eff.org/ "EFF: certbot") provide a simple new scheme for obtaining free, high-quality SSL certificates. Those certs are only valid for 90 days though, so regular renewals must be performed. Certbot leaves automating this up to end-user. Here's my take.

## Requirements
- certbot-auto, presumably installed in /etc/letsencrypt/certbot-auto

My certs were originally generated with `certbot-auto --standalone -d {domain}`, and stored in the default location.

## Usage
Place the `certbot-auto` script somewhere sensible (say, /etc/letsencrypt), mod it executable, and add it to your crontab. Certbot currently recommends scheduling it to run twice a day, at a random minute your choosing.
