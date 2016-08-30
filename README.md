# certbot-renew
A simple bash script I use to automate the renewal of Let’s Encrypt SSL certificates.

## Background
[Let's Encrypt](https://letsencrypt.org/ "Let's Encrypt") and its companion [certbot](https://certbot.eff.org/ "EFF: certbot") provide a  new scheme for obtaining free, high-quality SSL certificates. Those certs are only valid for 90 days though, so regular renewals must be performed. Certbot leaves automating this up to end-user. Here's my take.

## Requirements
- certbot-auto, presumably installed in /etc/letsencrypt/certbot-auto

My certs were originally generated with `certbot-auto --standalone -d {domain}`, and stored in the default location. I run Apache.

## Usage
Place the `certbot-auto` script somewhere sensible (say, /etc/letsencrypt). Review the `$LOG_FILE` and `$RENEW_CMD` settings to make sure they're right for your system. Mod it executable, and add it to your crontab. Certbot currently recommends scheduling it to run twice a day, at a random minute your choosing.

## Next Steps
- Run configtest before stopping Apache to increase the likelihood that it can be restarted safely
- Research certbot's `--http-01-port` arg as an alternative to stopping Apache
- Just learned about certbot's pre/post hooks, which can be used to start/stop Apache *only* if the cert actually needs updating. Cool!
- Only log stdout when there's a stderr (reduce noise in the log)
- Consider exposing `$LOG_FILE` via CLI

