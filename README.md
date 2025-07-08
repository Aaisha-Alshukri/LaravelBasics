# 📤 Laravel HTTP Responses – Branch: responses

This branch explains how to return and customize **HTTP Responses** in Laravel v12.x  
🔗 https://laravel.com/docs/12.x/responses

---

## 📌 Basic String or Array Response

Laravel automatically converts string or array return values to HTTP responses.

```php
Route::get('/', function () {
    return 'Hello World'; // Will return 200 OK with plain text
});
Returning arrays will be converted to JSON:
return ['status' => 'success'];

📄 View Responses
Return a view as a response:
return view('welcome');

Passing data:
return view('greeting', ['name' => 'Aaisha']);

📦 JSON Responses
return response()->json([
    'user' => 'John Doe',
    'email' => 'john@example.com'
]);

Setting status code:
return response()->json(['message' => 'Created'], 201);

🔁 Redirect Responses
return redirect('/dashboard');

Redirect to a named route:
return redirect()->route('home');

Redirect with data (flash):
return redirect()->back()->with('status', 'Profile updated!');

📥 File Downloads
return response()->download(public_path('manual.pdf'));
Rename the file while downloading:
return response()->download($path, 'NewName.pdf');

📎 File Response (Display in browser)
return response()->file(public_path('example.pdf'));

⚙️ Custom Response Headers
return response('Hello', 200)
            ->header('Content-Type', 'text/plain');

You can chain multiple headers:
->header('X-Custom', 'value')
->header('Cache-Control', 'no-cache');

🔧 Response Macros
You can define reusable response methods in a service provider:
Response::macro('caps', function ($value) {
    return Response::make(strtoupper($value));
});
Usage:
return response()->caps('hello world'); // returns "HELLO WORLD"

📋 Summary : 
Return views, strings, arrays, JSON, or files

Use response() helper for more control

Redirects and downloads are easily handled

You can customize headers or create macros







