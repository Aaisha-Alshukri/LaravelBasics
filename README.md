# 🛡️ Laravel CSRF Protection – Branch: csrf-protection

This branch focuses on Laravel's built-in **Cross-Site Request Forgery (CSRF) protection**, based on the official docs:  
🔗 https://laravel.com/docs/12.x/csrf

---

## ❓ What is CSRF?

CSRF (Cross-Site Request Forgery) is a type of attack where unauthorized commands are transmitted from a user that a web application trusts.  
It usually targets state-changing requests like form submissions.

Laravel automatically protects all **POST**, **PUT**, **PATCH**, and **DELETE** requests with CSRF tokens.

---

## 🔐 CSRF Middleware

The middleware responsible is:  
```php
\Illuminate\Foundation\Http\Middleware\VerifyCsrfToken::class


📝 Using CSRF Tokens in Forms: 
In Blade templates, always include @csrf inside forms:
<form method="POST" action="/submit">
    @csrf
    <!-- input fields -->
</form>
Alternatively, manually:
<input type="hidden" name="_token" value="{{ csrf_token() }}">


🧪 CSRF in Testing:
In feature tests, you can disable CSRF protection using:
$this->withoutMiddleware(
    \Illuminate\Foundation\Http\Middleware\VerifyCsrfToken::class
);

🚫 Excluding Routes from CSRF Protection:
÷n some cases (e.g., APIs or webhooks), you may want to exclude routes.

Edit the $except array in:
app/Http/Middleware/VerifyCsrfToken.php

-- Example:
protected $except = [
    'payment/webhook',
    'external-service/*',
];

🌐 CSRF with JavaScript (AJAX):
If  you're sending requests via JavaScript (Axios, jQuery, etc.), make sure to include the CSRF token in headers.

1. Add meta tag in Blade layout:
<meta name="csrf-token" content="{{ csrf_token() }}">

2. In JavaScript (example with Axios):
axios.defaults.headers.common['X-CSRF-TOKEN'] = 
    document.querySelector('meta[name="csrf-token"]').getAttribute('content');

📋 Summary:
CSRF protects your app from forged form submissions.

Always use @csrf in POST forms.

Middleware handles validation automatically.

Routes can be excluded if needed.

JavaScript requests must include the token in headers.




















