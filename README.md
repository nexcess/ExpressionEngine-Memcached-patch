ExpressionEngine-Memcached-patch
================================

Public repo for memcached patch for ExpressionEngine

## About

Changes ExpressionEngine to use [memcached](http://memcached.org/) for caching. Supports multiple memcached 
servers and UNIX socket server connections. Applies to these caches in ExpressionEngine:

  * Full-page cache (CodeIgniter component)
  * Database/Query cache
  * Version cache (for update checks)
  * Template/Tag cache
  * Channel cache

## Installation

Install by running the `patch` command with `-p 1` and the version of the patch that matches your version of 
ExpressionEngine from the base EE directory. The patch assumes that your system directory is called "system" 
so you will need to add a symlink if it has been renamed. Example:

~~~~bash
$ ls
admin.php  images  index.php  system  themes
$ patch -p1 < path/to/patch/ExpressionEngine-2.7.2_Memcached.patch
~~~~

## Configuration

The patch requires adding two settings to the ExpressionEngine config file:

  * `memcache_servers`: This is a comma-separated list of Memcached servers that should be used for caching. 
Sockets can be used by prefixing the path to the socket with `unix://`. Example: `localhost:11211,unix:///tmp/memcached.sock,10.0.100.200:11211`
  * `memcache_salt`: This is a salt used to hash cache keys and should be unique per ExpressionEngine site.

## Removal

The changes can be reversed by re-running the patch command.
