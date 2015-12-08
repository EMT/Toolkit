#Homestead

To get a Homestead project up and running on your local machine, follow these steps

1. Clone the project from GitHub into your local Homestead folder.

2. Run `homestead edit`. If this doesn't work, make sure composer is in your path, `PATH=~/.composer/vendor/bin:$PATH`

3. This should open your homestead config file in your text editor. To your list of sites, add something like following code:

  ```
    - map: myhome.dev
      to: /home/vagrant/homestead/myhome/public
  ```

  `map` is the development url, and `to` is the webroot of the project.

4. Making sure you're in the project root, run `npm install` and `composer install`.

5. In the project root, copy the `.env.example` file into a new file called `.env`.

6. Run `php artisan key-generate` to create an app key.

7. If you need to create any databases and/or users, create them on the virtual box using Sequel Pro.

8. If necessary, run migrations with `php artisan migrate` and seed with `php artisan  db:seed`

9. Run `gulp` to run the build tools.
