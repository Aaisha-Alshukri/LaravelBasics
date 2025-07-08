# 📤 Laravel HTTP Responses – Branch: responses

This branch explains how Laravel handles and returns **HTTP Responses**, based on the official Laravel 12.x documentation.  
🔗 https://laravel.com/docs/12.x/responses

---

## 📌 Basic Responses

You can return strings or arrays directly in routes or controllers.

```php
return 'Hello World';      // Simple text response
return ['name' => 'Salma']; // JSON response
Laravel automatically converts arrays to JSON.

🖼️ View Responses
Return Blade views using:
return view('welcome');
With data:
return view('profile', ['name' => 'Aaisha']);

📦 JSON Responses
Return structured JSON:
return response()->json([
    'status' => 'success',
    'user' => 'John Doe'
]);
With custom status code:
return response()->json(['message' => 'Created'], 201);

🔁 Redirect Responses
Redirect to URL:
return redirect('/home');

Redirect to route:
return redirect()->route('dashboard');

Redirect back with flash message:
return redirect()->back()->with('success', 'Saved!');

📥 File Downloads
To download a file:
return response()->download(public_path('file.pdf'));

With custom name:
return response()->download($path, 'custom-name.pdf');

📎 File Display
To show a file in the browser:
return response()->file(public_path('doc.pdf'));

🛠️ Custom Response Headers
You can customize headers like this:
return response('Hello', 200)
    ->header('Content-Type', 'text/plain')
    ->header('X-Custom', 'Value');

🧱 Response Macros
Define a reusable custom response:
Response::macro('caps', function ($value) {
    return Response::make(strtoupper($value));
});
Use it like this:
return response()->caps('hello'); // Outputs: HELLO


📋 Summary:

Strings, arrays, views, and JSON can all be returned easily.

Use response() for custom responses.

Laravel supports redirects, downloads, and custom headers.

You can even create reusable response macros.

















