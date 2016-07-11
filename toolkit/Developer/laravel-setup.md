## Laravel Setup

### 1. Composer Install

run `composer install`

### 2. npm install

Install Gulp + Elixer

```
npm install
```

### 3. Setup .env

Setup default .env file to stop any laravel errors.

run `cp .env.example .env`
run `php artisan key:generate`

You might also have to add a few other keys like Mailers/Twitter

### 4. (If using homestead)

Add site to hosts file, either manually or using a program like [Gas Mask](https://github.com/2ndalpha/gasmask).

Add site to homestead.yaml found at `~/.homestead`
run `vagrant up --provision`
