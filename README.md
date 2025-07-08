# 🛡️ Laravel Middleware – Branch: middleware

This branch explains and demonstrates the use of **Middleware** in Laravel 12.x  
🔗 Official Docs: https://laravel.com/docs/12.x/middleware

---

## 📌 What is Middleware?

Middleware acts as a **filter** for HTTP requests.  
It runs before or after a request hits your controller.

Used for things like:
- Authentication
- Logging
- CORS
- Maintenance mode
- Request modification

---

## 🧱 Built-in Middleware Examples

- `auth` – Ensures the user is authenticated
- `guest` – Redirects logged-in users
- `verified` – Ensures email is verified
- `throttle` – Limits request frequency (rate-limiting)

---

## 🛠️ Creating Middleware

```bash
php artisan make:middleware EnsureUserIsAdmin

Example:

public function handle($request, Closure $next)
{
    if (!auth()->user()?->isAdmin) {
        return redirect('/');
    }

    return $next($request);
}



🧩 Registering Middleware
➤ Global Middleware
Registered in app/Http/Kernel.php under $middleware

➤ Route Middleware
Registered in $routeMiddleware:

'admin' => \App\Http\Middleware\EnsureUserIsAdmin::class,

🧪 Using Middleware in Routes:
For a group of routes:
Route::middleware(['auth', 'admin'])->group(function () {
    Route::get('/admin/dashboard', ...);
});
For a single route:
Route::get('/profile', function () {
    // ...
})->middleware('auth');


⚙️ Middleware Parameters :
You can pass parameters to middleware:
Route::middleware('throttle:60,1')->group(function () {
    Route::get('/api/posts', ...);
});
//This means: 60 requests per 1 minute

🧹 Skipping Middleware in Tests:
$this->withoutMiddleware();
$this->withoutMiddleware([SomeMiddleware::class]);


📋 Summary: 
-Middleware filters requests before/after controller logic

-You can use built-in or custom middleware

-Middleware can be applied globally or to specific routes

-Parameters and route groups allow flexible usage




