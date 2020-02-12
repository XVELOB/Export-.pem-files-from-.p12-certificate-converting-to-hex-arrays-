# Export *.pem files from *.p12 certificate (converting into hex arrays)

Ingredients:
- *.p12 file
- linux console

## Export user_cert and user_key from *.p12 file
In your console type:
```
$ openssl pkcs12 -in cert.p12 -nocerts -out user_key.pem
$ openssl pkcs12 -in cert.p12 -clcerts -nokeys -out user_cert.pem
```	
At this point you have to type your password to proceed export both of files and type the new one for new *.pem files.

In the next step you sholud remove encryption from your user_key file. Type in console:
```
$ openssl rsa -in user_key.pem -out user_key_w.pem
```
In the last step you have to convert *.pem files into hex arrays. Just type in cosole:
```
$ xxd –i user_key_w.pem user_key.txt
$ xxd –i user_cert.pem user_cert.txt
```
Done. Now you can use your hex arrays e.g. to connect to the WPA2 Enterprise with ESP.
