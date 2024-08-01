
# Version laravel 

Installing laravel/laravel (v10.3.3)

## change sqlite

- create a file .env (copy .env.example )

[SQLITE](https://github.com/artisan24fullstack/laravelStepByStep/tree/main/hike)

```
php artisan migrate
```

- create in folder database, a file database.sqlite

## Installation Laravel Jestream (blade)

[Jestream official](https://jetstream.laravel.com/installation.html)

[Repo Jestream](https://github.com/artisan24fullstack/automatisationLaravel/tree/main/authLaravel)


### Installing Jetstream , Install Jetstream With Livewire ​with blade

```
composer require laravel/jetstream
php artisan jetstream:install livewire
```


if ERROR NEXT, git add . 

```
warning: in the working copy of 'workshopBecode/config/app.php', CRLF will be replaced by LF the next time Git touches it
warning: in the working copy of 'workshopBecode/package.json', CRLF will be replaced by LF the next time Git touches it
```

if ERROR NEXT

```
SQLSTATE[HY000]: General error: 1 no such table: sessions
select * from "sessions" where "id" = LfpI71yZKDdK7VOuMfNLaxQK0uDMnWlFR0Ht5mYK limit 1
```

### Finalizing the Installation ​

> npm install

> php artisan migrate

```

added 147 packages, and audited 148 packages in 8s

36 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities


   INFO  Running migrations.

  2014_10_12_200000_add_two_factor_columns_to_users_table ............................................... 14ms DONE
  2024_07_31_115350_create_sessions_table ............................................................... 13ms DONE
```

If ERROR NEXT, 
> npm run dev

```
Illuminate
 \ 
Foundation
 \ 
ViteManifestNotFoundException
PHP 8.1.10
10.48.18
Vite manifest not found at: C:\workshopBecode\public\build/manifest.json
```

> php artisan serve 

- application laravel with Log in and Register

> Installation (concurrently)

- add code next for (update scripts package json)

```
npm i concurrently -g

"start": "concurrently  \"php artisan config:cache\" \"php artisan serve\" \"npm run dev \"  "


scripts": {
        "dev": "vite",
        "build": "vite build",
        "start": "concurrently  \"php artisan config:cache\" \"php artisan serve\" \"npm run dev \"  "

    },
```

### Installation Filament

```
composer require filament/filament:"^3.0"

php artisan filament:install --panels
```


PREPARE Resources for workshop (BACKEND)

### Proposal and to test (TODO)

- To leverage PHP Enums in Laravel, Jetstream, and Filament for managing roles like ADMIN, EDITOR, and USER in your User model, follow these steps:


- Leveraging PHP Enums in Laravel with the iteks/laravel-enum Package
https://medium.com/@jeramyhing/leveraging-php-enums-in-laravel-with-the-iteks-laravel-enum-package-e826cca6e357

> Step 1: Define Enum Classes
- First, create separate Enum classes for roles and permissions. 
- This will help in maintaining a clean and organized structure for role management.


```
<?php

namespace App\Enums;

enum Role: string
{
    case ADMIN = 'ADMIN';
    case EDITOR = 'EDITOR';
    case USER = 'USER';

    public static function labels(): array
    {
        return [
            self::ADMIN => 'Admin',
            self::EDITOR => 'Editor',
            self::USER => 'User',
        ];
    }

    // Static property to hold the default role
    public static string $ROLE_DEFAULT = self::USER;
}

enum Permission: string
{
    case VIEW_ADMIN = 'view-admin';
}

```

> Step 2: Update the User Model
- Modify the User model to use these enums instead of constants. 
- Also, update the methods to utilize these enums effectively.


```
use App\Enums\Role;
use App\Enums\Permission;

   public function canAccessPanel(Panel $panel): bool
    {
        return $this->hasPermission(Permission::VIEW_ADMIN);
    }

    public function isAdmin(): bool
    {
        return $this->role == Role::ADMIN;
    }

    public function isEditor(): bool
    {
        return $this->role == Role::EDITOR;
    }
```

> Step 3 How to Use $ROLE_DEFAULT in migration

```
<?php

use Illuminate\Support\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Database\Migrations\Migration;

// Import the Role enum
use App\Enums\Role;

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::table('users', function (Blueprint $table) {
            // Use the $ROLE_DEFAULT property from the Role enum
            $table->string('role')->default(Role::$ROLE_DEFAULT);
        });
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::table('users', function (Blueprint $table) {
            $table->dropColumn('role');
        });
    }
};
```
