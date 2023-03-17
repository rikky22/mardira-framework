<!-- write title Mardira Framework -->

<p align="center"><a href="https://demostmikmi.com" target="_blank"><img src="https://raw.githubusercontent.com/Bootcamp-STMIK-Mardira-Indonesia/mardira-framework/master/public/logo.png" width="150" alt="Mardira Logo"></a></p>

<!-- Description here -->

Mardira Framework is a PHP framework Model Controller Based for building web applications and APIs. It is designed to be simple, and fast.

![Total Downloads](https://img.shields.io/packagist/dt/mardira/mardira-framework?color=e&style=for-the-badge)
![Total Stars](https://img.shields.io/github/stars/Bootcamp-STMIK-Mardira-Indonesia/mardira-framework?color=e&style=for-the-badge)
![Total Forks](https://img.shields.io/github/forks/Bootcamp-STMIK-Mardira-Indonesia/mardira-framework?color=e&style=for-the-badge)
![Version](https://img.shields.io/packagist/v/mardira/mardira-framework?color=e&style=for-the-badge)
![License](https://img.shields.io/github/license/Bootcamp-STMIK-Mardira-Indonesia/mardira-framework?color=e&style=for-the-badge)

## Table of Contents

- [Requirements](#requirements)
- [Structure Folders](#structure-folders)
- [Installation](#installation)
- [Usage](#usage)
  - [Start Server](#start-server)
  - [Create .env](#create-env)
  - [Create Controller](#create-controller)
  - [Create Model](#create-model)
  - [Create Migration](#create-migration)
  - [Run Migration](#run-migration)
  - [Refresh Migration](#refresh-migration)
  - [Refresh Migration With Seed](#refresh-migration-with-seed)
  - [Create Seeder](#create-seeder)
  - [Run Seeder](#run-seeder)
  - [Run Seeder Specific](#run-seeder-specific)
  - [Create Authetication](#create-authetication)
  - [Refresh Authetication](#refresh-authetication)
  - [Update Framework Version](#update-framework-version)
  - [Controller](#controller)
  - [Model](#model)

## Requirements

- PHP >= 7.4
- MySQL >= 5.7.8
- Apache >= 2.4.41
- Composer >= 2.0.9

## Structure Folders

```shell
mardira-framework
├── App
│   ├── Controllers
│   │   ├── AuthController.php
│   ├── Core
│   │   ├── Commands
│   ├── Database
│   │   ├── Migrations
│   │   │   ├── 2023_01_31_xxxxxx_create_table_users.php
│   │   │   ├── 2023_01_31_xxxxxx_create_table_roles.php
│   │   ├── Seeders
│   │   │   ├── GlobalSeeder.php
│   ├── Helpers
│   ├── Middleware
│   ├── Models
│   ├── Packages
│   ├── Routes
│   │   ├── Api.php
```

## Installation

<!-- Installation here -->

### Clone

- Clone this repo to your local machine using `git clone

```shell
  git clone https://github.com/Bootcamp-STMIK-Mardira-Indonesia/mardira-framework.git
```

> Then, install the dependencies using composer

```shell
composer install
```

> or

```shell
composer update
```

### Setup

> You can create a new project using composer

```shell
composer create-project mardira/mardira-framework <your_project_name>
```

## Usage

### Start Server

```shell
php mardira serve
```

> or

```shell
php mardira serve --port=<your_port>
```

### Create .env

> You can create .env file using command

```shell
php mardira make:env
```

### Create Controller

```shell
php mardira make:controller ControllerName
```

### Create Model

```shell
php mardira make:model ModelName
```

### Create Migration

```shell

php mardira make:migration create_table_table_name
```

### Run Migration

> If database not exist, will automatically create database from .env

```shell
php mardira migrate
```

### Refresh Migration

```shell
php mardira migrate:refresh
```

### Refresh Migration With Seed

```shell
php mardira migrate:refresh --seed
```

### Create Seeder

```shell
php mardira make:seeder SeederName
```

### Run Seeder

```shell
php mardira db:seed
```

### Run Seeder Specific

```shell
php mardira db:seed --class=SeederName
```

### Create Authetication

```shell
php mardira make:auth
```

### Refresh Authetication

```shell
php mardira make:auth --refresh
```

### Update Framework Version

```shell
php mardira update
```

### Controller

> Create controller use `php mardira make:controller ControllerName`, here is example controller

```php
<?php

namespace App\Controllers;

use App\Core\Controller;

class HomeController extends Controller
{
    public function index()
    {
        $this->response->json(200,[
            'message' => 'Hello World'
        ]);
    }
}
```

> to use controller, you can add route in `App/Routes/Api.php`

```php
<?php

use App\Core\Route;
use App\Controllers\HomeController;

Route::get('/home', [HomeController::class, 'index']);
```

### Response

> You can use response in controller

```php
$this->response->json(200,[
    'message' => 'Hello World'
]);

```

> return json expected

```json
{
  "message": "Hello World"
}
```

> another response example 409

```php
$this->response->json(409,[
    'message' => 'Conflict'
]);
```

### Model

> Create model use `php mardira make:model ModelName`, here is example model

```php
<?php

namespace App\Models;

use App\Core\Model;

class User extends Model
{
    protected $table = 'users';
    protected $primaryKey = 'id';
}
```

> to use model, you can add model in `App/Controllers/ControllerName.php`

```php
<?php

namespace App\Controllers;

use App\Core\Controller;
use App\Models\User;

class HomeController extends Controller
{
    public function index()
    {
        $user = User::all();

        $this->response->json(200,[
            'message' => 'Hello World',
            'data' => $user
        ]);
    }
}
```


## Support

Reach out to me at one of the following places!

- Website at <a href="https://demostmikmi.com" target="_blank">`demostmikmi.com`</a>
