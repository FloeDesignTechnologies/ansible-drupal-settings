Drupal Settings
===============

Ansible role to manage Drupal `settings.php` files.

Features
--------
* Generate complete `settings.php` using Ansible variables.
  * Database settings
  * Hash salt
  * Base URL
  * PHP settings
  * Cookie domain
  * Variable overrides
  * Files includes
* [Multi-sites](https://www.drupal.org/documentation/install/multi-site) support (with [aliasing](https://api.drupal.org/api/drupal/sites!example.sites.php/7))


Role Variables
--------------

```
# The path to the sites folder where to create 
drupal_settings_basedir: /var/www/sites

# The sites settings, as a hash of sites
drupal_settings_sites:
  default:
    # Variable overrides (ie. $conf) as a hash
    # Currently only support only array (as nested hash) and string values
    conf: {}
    # Database settings
    # Currently only support only array (as nested hash) and string values
    databases: {}
    # PHP settings (ini_set('{{ key }}', '{{ value }}')) as a hash
    # Currently only support string values
    php_ini: {}
    # Salt for one-time login links and cancel links, form tokens, etc. as a string
    hash_salt: "{{ lookup('password') }}"
    # Base URL as a string (optional)
    base_url: www.example.com
    # Cookie domain as a string (optional)
    cookie_domain: .example.com
    # Whether or not to enable fast 404 as a boolean (optional)
    fast_404: false
    # Site aliases (for sites.php) as a list of strings (optional)
    aliases: []
    # Includes (path to PHP file ton require_once) as a list of strings (optional)
    includes: []

# Default settings for all sites
drupal_settings_default:
  # Variable overrides (ie. $conf) as a hash
  # Currently only support only array (as nested hash) and string values
  conf:
    404_fast_paths_exclude: '/\/(?:styles)\//';
    404_fast_paths: '/\.(?:txt|png|gif|jpe?g|css|js|ico|swf|flv|cgi|bat|pl|dll|exe|asp)$/i';
    404_fast_html: '<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML+RDFa 1.0//EN" "http://www.w3.org/MarkUp/DTD/xhtml-rdfa-1.dtd"><html xmlns="http://www.w3.org/1999/xhtml"><head><title>404 Not Found</title></head><body><h1>Not Found</h1><p>The requested URL "@path" was not found on this server.</p></body></html>';
  # PHP settings (ini_set('{{ key }}', '{{ value }}')) as a hash
  # Currently only support string values
  php_ini:
    session.gc_probability: 1
    session.gc_divisor: 100
    session.gc_maxlifetime: 200000
    session.cookie_lifetime: 2000000
  # Includes (path to PHP file ton require_once) as a list of strings (optional)
  includes: []
```

License
-------

Apache v2

Author Information
------------------

* Pierre Villette (villette@floedesign.ca)
* Pierre Buyle (buyle@floedesign.ca)
