<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/Labs64/laravel-boilerplate"><img src="https://travis-ci.org/Labs64/laravel-boilerplate.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/labs64/laravel-boilerplate"><img src="https://poser.pugx.org/labs64/laravel-boilerplate/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/labs64/laravel-boilerplate"><img src="https://poser.pugx.org/labs64/laravel-boilerplate/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/labs64/laravel-boilerplate"><img src="https://poser.pugx.org/labs64/laravel-boilerplate/license.svg" alt="License"></a>
</p>

# Laravel 5 Boilerplate Project

_Laravel Boilerplate_ provides a very flexible and extensible way of building your custom Laravel 5 applications.

## MAIL OPTIONS error ssl
C:\projectname\vendor\swiftmailer\swiftmailer\lib\classes\Swift\Transport\StreamBuffer.php
and find out this function inside StreamBuffer.php

private function _establishSocketConnection()
and paste this two lines inside of this function

$options['ssl']['verify_peer'] = FALSE;
$options['ssl']['verify_peer_name'] = FALSE;
and reload your browser and try to run your project again. For me I put on like this:

```
private function _establishSocketConnection()
{
    $host = $this->_params['host'];
    if (!empty($this->_params['protocol'])) {
        $host = $this->_params['protocol'].'://'.$host;
    }
    $timeout = 15;
    if (!empty($this->_params['timeout'])) {
        $timeout = $this->_params['timeout'];
    }
    $options = array();
    if (!empty($this->_params['sourceIp'])) {
        $options['socket']['bindto'] = $this->_params['sourceIp'].':0';
    }

   $options['ssl']['verify_peer'] = FALSE;
    $options['ssl']['verify_peer_name'] = FALSE;
}
```


## Minimum System Requirements
To be able to run Laravel Boilerplate you have to meet the following requirements:
- PHP > 5.6.4
- PHP Extensions: PDO, cURL, Mbstring, Tokenizer, Mcrypt, XML, GD
- Node.js > 6.0
- Composer > 1.0.0
- Bower

## Installation
1. Install Composer using detailed installation instructions [here](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
2. Install Node.js using detailed installation instructions [here](https://nodejs.org/en/download/package-manager/)
3. Clone repository
```
$ git clone https://github.com/Labs64/laravel-boilerplate.git
```
4. Change into the working directory
```
$ cd laravel-boilerplate
```
5. Install dependencies
```
$ composer install --prefer-dist
$ npm install
```
6. Edit `.env.example` according to your environment and save as `.env`
7. An application key can be generated with the command
```
$ php artisan key:generate
```
8. Execute following commands
```
$ bower install
$ npm run dev
```
9. Run these commands to create the tables within the defined database and populate seed data
```
$ php artisan migrate --seed
```
If you get an error like a `PDOException` try editing your `.env` file and change `DB_HOST=localhost` to `DB_HOST=127.0.0.1`.

