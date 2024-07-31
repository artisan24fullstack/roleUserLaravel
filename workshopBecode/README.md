
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

[Repo Jestream](https://github.com/artisan24fullstack/laravelStepByStep/tree/main/hike)


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
