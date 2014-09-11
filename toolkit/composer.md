# Composer

Composer is a PHP package manager. We use it with PHP projects to manage dependencies and libraries, and make it easy to deploy to various environments.

To set up on OS X:

1. Change into a directory in your path like: `cd /usr/local/bin`
2. Get Composer: `curl -sS https://getcomposer.org/installer | php`
3. Make the phar executable: `sudo chmod a+x composer.phar`
4. Rename the composer.phar to composer: `sudo mv composer.phar composer`

To install composer packages for a project:

1. Change into your project directory: `cd /path/to/my/project`
2. Run install: `composer install`

Have a look at [the docs](https://getcomposer.org/doc/00-intro.md) for more on using Composer.