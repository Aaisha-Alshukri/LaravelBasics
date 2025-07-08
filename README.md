# 📥 Laravel HTTP Requests – Branch: requests

This branch explains how to work with **HTTP Requests** in Laravel (v12.x), based on the official documentation:  
🔗 https://laravel.com/docs/12.x/requests

---

## 📌 Introduction

Laravel provides a simple and elegant way to handle **incoming HTTP requests**.

Request data can be accessed using the `Illuminate\Http\Request` class, which is automatically injected into controller methods or route closures.

---

## 🧾 Accessing Request Data

Inject the request:

```php
use Illuminate\Http\Request;

public function store(Request $request)
{
    $name = $request->input('name');
}

Other Methods:
$request->all();
$request->only(['name', 'email']);
$request->has('name');
$request->filled('email');

🛡️ Request Validation (Inline)
You can validate request data directly:
$request->validate([
    'title' => 'required|max:255',
    'content' => 'required',
]);
If validation fails, Laravel redirects back with errors automatically.

🔄 Old Input & Flash Data
Laravel automatically "flashes" input data to the session when validation fails.

In Blade:
<input type="text" name="title" value="{{ old('title') }}">

You can also manually flash data:
$request->flash();

✅ Checking Request Type
$request->isMethod('post');      // true or false
$request->method();              // Returns 'GET', 'POST', etc.
$request->ajax();                // Checks if request is AJAX
$request->wantsJson();           // Checks if JSON response is expected

🌐 Working with URLs and Paths
$request->path();                // e.g. 'blog/post'
$request->url();                 // full URL
$request->fullUrl();            // URL + query string
$request->query('page');        // get query parameter

🧱 File Uploads
$request->file('avatar');       // Get uploaded file
$request->hasFile('avatar');    // Check if file was uploaded

Example:
$request->file('avatar')->store('avatars');

🔐 Authorization via Form Inputs
You can include authorization logic in custom form requests or directly in controller methods.

📋 Summary
Use the Request class to access input, files, headers, and method types

Support for validation, flashing old input, and more

Works seamlessly with controllers and route closures















