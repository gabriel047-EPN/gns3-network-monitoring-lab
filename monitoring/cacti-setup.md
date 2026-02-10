Alias /cacti /var/www/html/cacti

<Directory /usr/share/cacti/site>
    Options +FollowSymLinks
    AllowOverride None
    Require all granted

    AddType application/x-httpd-php .php

    <IfModule mod_php7.c>
        php_flag magic_quotes_gpc Off
        php_flag short_open_tag On
        php_flag register_globals Off
        php_flag register_argc_argv On
        php_flag track_vars On
        # this setting is necessary for some locales
        php_value mbstring.func_overload 0
        php_value include_path .
    </IfModule>
</Directory>

DirectoryIndex index.php





Alias /cacti /var/www/html/cacti

<Directory /var/www/html/cacti>
    Options +FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>

DirectoryIndex index.php
