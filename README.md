# Wordpress deploy plugin  for Dokku

Adding persistent storage for apps, loads mysql dump, sets custom url for apps.
##Install

    cd /var/lib/dokku/plugins
    git clone https://github.com/nea88/dokku_wp_deploy-plugin
    dokku plugins-install
    
##Simple usage
    Put in your /wp-config.php
    
        extract(parse_url($_ENV["DATABASE_URL"]));
        define( 'WP_LOCAL_DEV', false );
        define( 'DB_NAME', substr($path, 1) );
        define( 'DB_USER', $user );
        define( 'DB_PASSWORD', $pass );
        define( 'DB_HOST', $host );
        
    /PERSISTENT_STORAGE 
        $/home/dokku/.storages/project_name:/app/content/uploads:rw
    /PROJECT_NAME
        project_name
    /project_name.mysql with mysql dump

And then just push your app




##Dependences
mysql
mysqldump
https://github.com/Nea88/dokku_mysql_wp_plugin.git
https://github.com/Nea88/dokku_mysql_dump-plugin.git
https://github.com/wmluke/dokku-domains-plugin.git
