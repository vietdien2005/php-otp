PHPOTP
======

Php Implementation of the OTP algorythm

# Generating a secret
secret = Base32::encode("yourrandomsecretkey")

#Google authenticator
Google provides Android and iPhone application that generates the verification code for the user.

#Validating the integrity

```php
<?php
	require_once("rfc6238.php");
	
	$secretkey = 'GEZDGNBVGY3TQOJQGEZDGNBVGY3TQOJQ';  //your secret code
	$currentcode = '571427';  //code to validate, for example received from device


	
	if (TokenAuth6238::verify($secretkey,$currentcode))
	{
		echo "Code is valid\n";
	}
	else
	{
		echo "Invalid code\n";
	}
```

#Generating the code

```print TokenAuth6238::getTokenCodeDebug($secretkey,0);```


#Generating the QRCode for GOOGLE Authenticator

```print sprintf('<img src="%s"/>',TokenAuth6238::getBarCodeUrl('','',$secretkey));```
