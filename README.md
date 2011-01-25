# oversky
Decentralized HTTP content delivery network (CDN) coded in PHP

## Description
oversky is a decentralized HTTP content delivery network implemented in PHP. It is based on a distributed 
hash table (DHT) and, being fully implemented on top of HTTP, its use is transparent to any HTTP client.

It can be used to provide load balancing, geographic redundancy, distributed caching or even as an
integration to the DNS system.

## Current status
This is currently pre-alpha software. All specifications may still be 
subject to change. Do not use in production environments!

Please note that even if it is designed to be as generic and compatible
as possible, it's still under heavy development and has not been fully
tested. oversky is being developed on Linux x64, Apache 2, PHP 5.2,
MySQL 5.1: compatibility with other systems/softwares has not been tested.

All files of the oversky repository are covered by the GPLv3 license.

## Installation
To run oversky you'll need:

*   a working Apache installation
*   PHP 5 (with the mcrypt and PDO modules) 
*   a working databse with the relative PDO driver

The first step is to configure your oversky instance: open the `oversky.configuration.phpi.template` file
and fill in all the settings (see the comments in that file for instructions). Save the modified file as
`oversky.configuration.phpi`.

When done, request `oversky.php?action=setup` from your browser. This performs a few sanity checks and 
sets up the working directories and database. If no error is reported and you're redirected to the 
welcome page you should have a working oversky instance.

## Bootstrapping
Once you have a working instance, you need to connect it to the oversky 
DHT. Until autodiscovery is implemented, you'll need to manually find another 
instance that is already connected to the oversky DHT. Then, by 
requesting `oversky.php?action=hostdiscovery&host=<URL of instance>` that
instance will be added to the known hosts list.

## Registering files
To add a static HTTP resource to the DHT, request `oversky.php?action=register&location=<file or URL>`.
A copy of the or resource identified by the URL will be created in the working private directory, and 
the file will be uniquely identified by the SHA-256 hash of its contents.

## Geting files
To get a file you can request `oversky.php?action=get&key=<SHA-256 hash of file>` on any instance of the 
oversky DHT: the network will look for a node with a copy of the resource and seamlessly redirect your 
browser to that resource.
