# oversky
DHT built in PHP meant to be used as a decentralized HTTP CDN

## Current status
This is currently pre-alpha software. All specifications may still be 
subject to change. Do not use in production environments!

All files of the oversky repository are covered by the GPLv3 license.

## Installation
To run oversky you'll need:

*   a working Apache installation
*   PHP 5 (with the mcrypt and PDO modules) 
*   a working databse with the relative PDO driver

The first step is configure your oversky instance: to do so, open `oversky.configuration.phpi.template`
and fill in all the settings (see the comments in the file for information). Save the modified file as
`oversky.configuration.phpi`.

When done, request `oversky.php?action=setup` from your browser. This performs a few sanity checks and 
sets up the working directories and database. If no error is reported and you're redirected to the 
welcome page you should now have a working oversky instance.

## Bootstrapping
Once you have a working instance, you need to connect it to the oversky 
DHT. Until autodiscovery is implemented, you'll need to find another 
instance that is already connected to the oversky DHT. Then, by 
requesting `oversky.php?action=hostdiscovery&host=<URL of instance>` that
instance will be added to the known hosts list.

## Registering files
To add a local file or HTTP resource to the DHT, request `oversky.php?action=register&location=<file or URL>`.
A copy of the file (or resource identified by the URL) will be created in the working private directory, and 
the file will be uniquely identified by the SHA-256 hash of its contents.

## Geting files
To get a file you can request `oversky.php?action=get&key=<SHA-256 hash of file>` on any instance of the 
oversky DHT.
