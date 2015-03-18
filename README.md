Drupal Settings
===============

Ansible role to manage Drupal settings.


Role Variables
--------------

```
drupal_settings_sites:
  default:
    conf: {}
    databases: {}
    php: {}
    hash_salt: "{{ lookup('password') }}"
    fast_404: false

drupal_settings_default:
  conf:
    404_fast_paths_exclude: '/\/(?:styles)\//';
    404_fast_paths: '/\.(?:txt|png|gif|jpe?g|css|js|ico|swf|flv|cgi|bat|pl|dll|exe|asp)$/i';
    404_fast_html: '<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML+RDFa 1.0//EN" "http://www.w3.org/MarkUp/DTD/xhtml-rdfa-1.dtd"><html xmlns="http://www.w3.org/1999/xhtml"><head><title>404 Not Found</title></head><body><h1>Not Found</h1><p>The requested URL "@path" was not found on this server.</p></body></html>';
  php:
    session.gc_probability: 1
    session.gc_divisor: 100
    session.gc_maxlifetime: 200000
    session.cookie_lifetime: 2000000
  includes []
```

License
-------

Apache v2

Author Information
------------------

Pierre Villette
