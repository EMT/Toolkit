Lithium Apps
============

The database credentials for a Lithium app are stored in

    /app/config/boostrap/connections.php

You can set up a new database and corresponding user through [phpMyAdmin](http://localhost:8888/phpMyAdmin/)

Once the database has been set up, run the migrations by visiting

    [project-url]/console/migrate/li3_auth

(This makes sure all our local databases are kept in sync.)