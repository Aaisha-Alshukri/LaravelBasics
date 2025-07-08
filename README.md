# 🧭 Laravel Controllers – Branch: controllers

This branch focuses on how to use **Controllers** in Laravel (v12.x), based on the official documentation:  
🔗 https://laravel.com/docs/12.x/controllers

---

## 📌 What are Controllers?

Controllers are PHP classes used to group related request handling logic into a single class.  
They help organize your application by separating routing from logic.

Instead of defining logic in routes:

```php
Route::get('/users', function () {
    return User::all();
});

You define it in a controller method:
Route::get('/users', [UserController::class, 'index']);


🛠️ Creating a Controller: Use Artisan to generate controllers:
php artisan make:controller UserController 
-- This creates a file in app/Http/Controllers/UserController.php

🧩 Controller Methods Example
class UserController extends Controller
{
    public function index()
    {
        return User::all();
    }

    public function show($id)
    {
        return User::findOrFail($id);
    }
}

📦 Resource Controllers : Use the --resource flag to create CRUD methods automatically:

php artisan make:controller ProductController --resource

لإhis creates methods like:

index()

create()

store()

show()

edit()

update()

destroy()

Register as a resource route:
Route::resource('products', ProductController::class);

🎛️ Invokable Controllers:
For single-action controllers:
php artisan make:controller ShowProfile --invokable

Use in route:
Route::get('/profile', ShowProfile::class);

🛡️ Controller Middleware : 
You can apply middleware to controllers:
public function __construct()
{
    $this->middleware('auth');
}
Apply only to specific methods:
$this->middleware('auth')->only('store');
$this->middleware('admin')->except('index');

🧪 Route-Model Binding in Controllers
Laravel can automatically inject models into controller methods:
public function show(User $user)
{
    return $user;
}
This uses the {user} parameter in the route.

📋 Summary

Controllers help organize logic cleanly

Use php artisan make:controller to generate them

Use resource controllers for CRUD

Support middleware, model binding, and more





























