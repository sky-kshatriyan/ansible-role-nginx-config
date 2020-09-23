# Changelog

## 0.2.0 (September 23, 2020)

BREAKING CHANGES:

*   The process to configure modules has changed. Instead of manually setting the modules you want to install to `true` or `false`, you will now have to use either:
    *   A newly introduced top level list variable, `nginx_config_modules`.
    *   A newly introduced list variable within your main NGINX config template, `nginx_config_main_template.modules`.

Make sure you only use one variable or the other, since they will overwrite each other. This change will simplify adding future supported modules to this role, and allows you to include any external modules you may wish in your NGINX config.

FEATURES:

*   Support for all NGINX App Protect directives has been added. You can find details on the supported directives on `defaults/main/template.yml`. This is the first module to be included using J2 macros. Expect to slowly see a refactor of various modules to use macros where possible.
*   Add Alpine `3.12` to the list of supported platforms.
*   Remove Alpine `3.8` from the list of supported platforms .
*   Add NGINX Plus tests to TravisCI

ENHANCEMENTS:

*   Added handlers to check for NGINX syntax validity and fail if any errors are detected.
*   Switch to using `ansible_facts` wherever possible.
*   Improved tasks naming conventions.
*   Update Ansible to `2.9.13` and Ansible Lint to `4.3.5`.
*   Explicitly defined `mode` in relevant tasks.
*   Improve configuration templating capabilities:
    *   Allow setting `access_log`/`access_log_location` to `off`.
    *   Add IP restriction for web servers

BUG FIXES:

*   An empty `nginx_config_cleanup_files` will no longer cause `nginx_config_cleanup` related tasks to fail.

## 0.1.0 (August 19, 2020)

Initial release of the NGINX Config role. Contains all NGINX Config related features previously available on the [NGINX Ansible role](https://github.com/nginxinc/ansible-role-nginx).
