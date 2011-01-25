# oversky
DHT built in PHP meant to be used as a decentralized HTTP CDN

## Current status
This is currently pre-alpha software. All specifications may still be 
subject to change. Do not use in production environments!

All files of the oversky repository are covered by the GPLv3 license.

## Installation
To run oversky make sure you'll need a working Apache installation with 
PHP 5 (with the mcrypt and PDO modules) and a working databse with the 
relative PDO driver.

The first step is configure your oversky instance: to do so, rename the 
`oversky.configuration.phpi.template` to `oversky.configuration.phpi` 
and fill in the needed informations.

When done, request `oversky.php?action=setup` from your browser. If no 
error is reported and you're redirected to the welcome page you 
should now have a working oversky instance.
