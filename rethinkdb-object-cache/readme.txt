=== Plugin Name ===
Contributors: withinboredom
Tags: rethinkdb, objectcache, object, cache
Requires at least: 4.0
Tested up to: 4.0
Stable tag: trunk
License: GPLv2
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Use rethinkdb as an object cache

== Description ==

This plugin enables the ability to use rethinkdb as an object cache. Rethinkdb is an easy to scale, distributed,
key/value store. Find out more about it here: https://rethinkdb.com

Caveats:

1. Rethinkdb is a disk based persistent store, the plugin does best effort to remove stale objects.
2. Throughput is extremely high with a single shard and multiple replica. Your miliage may vary.
3. Consider this plugin experimental for now.
4. This will override any other object cache you are using, such as those found in other caching plugins.

== Installation ==

This guide assumes you've already set up and configured a rethinkdb server(s). It's recommended that you've set up at
least three servers. Best throughput in the lab was with 3 servers, 1 database, 1 table with 1 shard and 3 replicas.

1. Copy the plugin to `wp-content/muplugins/rethinkdb-object-cache`
2. Copy object-cache.php to `wp-content/object-cache.php`
3. Define these variables in `wp-config.php`:

``` php
define('RETHINK_HOST', '/* Put the ip address or hostname of ONE rethinkdb server, the rest is magic */');
define('RETHINK_DB', 'cache'); // you can change the name to use a different database
define('RETHINK_TABLE', 'objectstore'); // you can change the name to use a different table
```

Congratulations, you've now setup rethinkdb to be a wordpress object cache.

== Frequently Asked Questions ==

= How fast is it? =

Tests show that its about 4 times slower than memcached. We'll work on making it faster...

= Why? Just why? =

With rethinkdb, another service can subscribe to changes. This opens some very interesting doors in the future. Such as
triggering specific jobs when a post is created, or a sale made.

Also, through the rethinkdb ui, it's very easy to get visibility into exactly what is cached, which can be useful in development.

= I'm having problems, can you help me? =

Feel free to contact me in the support forums here on the plugin page.

== Changelog ==

= 0.1.0 =
* rethinkdb inital release
