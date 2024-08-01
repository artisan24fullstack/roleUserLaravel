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
