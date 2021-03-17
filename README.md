sudo yum install postfix cyrus-sasl cyrus-sasl-lib cyrus-sasl-plain
mkdir /etc/postfix/sasl/
vi /etc/postfix/sasl/sasl_passwd
[smtp.gmail.com]:587 Email:Pass   //write this in sasl_passwd file
postmap /etc/postfix/sasl/sasl_passwd
ls -la
ls -la /etc/postfix/sasl/sasl_passwd
cd /
cd  /etc/postfix/sasl/sasl_passwd
cd  /etc/postfix/sasl/
ls -la
sudo chown root:root /etc/postfix/sasl/sasl_passwd /etc/postfix/sasl/sasl_passwd.db
chmod 0600 /etc/postfix/sasl/sasl_passwd /etc/postfix/sasl/sasl_passwd.db
postconf -e relayhost=[smtp.gmail.com]:587
postconf -e smtp_sasl_auth_enable=yes
postconf -e smtp_sasl_security_options=noanonymous
postconf -e smtp_sasl_passwd_maps=hash:/etc/postfix/sasl/sasl_passwd
postconf -e smtp_tls_security_level=encrypt
postconf -e smtp_tls_security_level=verify
postconf -e smtp_tls_CAfile=/etc/ssl/certs/ca-bundle.crtls





