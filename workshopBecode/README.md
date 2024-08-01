
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
- npm start

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

### Create a user (admin)

#### Allowing users to access a panel

[Doc](https://filamentphp.com/docs/3.x/panels/installation)


> php artisan make:filament-user
- https://filamentphp.com/docs/3.x/panels/installation#create-a-user

```
 Name:
 Email address:
 Password:

   INFO  Success! (email adresse) may now log in at http://localhost:8000/admin/login.
```

----------------------------------------------------


PREPARE Resources for workshop (BACKEND)

> To find out more (ENUMS)
[Doc ENUMS](https://github.com/artisan24fullstack/roleUserLaravel/blob/main/workshopBecode/enums.md)
