# acme-webhook

NOTE: 
only tried this on OPNsense 24.7 when published


## Steps
Follow the steps below on the opnsense shell.

1. Create custom scripts directory
```
mkdir -p /usr/opnsense/<your_custom_foldername>
```
2. Copy upgrade script to the folder in step #1
3. Create folder for adguard cert config
```
mkdir -p /usr/local/AdGuardHome/certs
```
4. Copy actions conf file to the `/usr/local/opnsense/service/conf/actions.d` folder
5. Restart configd using command 
```
service configd restart
```
6. Now configure CronJob `System ‣ Settings ‣ Cron`
7. Configure Adguard > Encryption Settings as follows:
```
Certificates > Set a certificates file path > /usr/local/AdGuardHome/certs/fullchain.pem
Private key > Set a private key file > /usr/local/AdGuardHome/certs/private.key
```
This will ensure you dont have to keep changing Adguard cert paths when cert is renewed.

NOTE: Run this script manually the first time after generating your certificate using acme.sh or when implementing this script for the first time.
