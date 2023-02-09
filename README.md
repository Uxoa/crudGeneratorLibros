
## CRUD done in 20 mins.

Thank you to https://github.com/awais-vteams/laravel-crud-generator I have done this clean and quick CRUD.

## Installation & Configuration

- composer create-project laravel/laravel  nombreDeProyecto
- php artisan make:migration libros
- folder migrations > abrir la migracion nueva y escribir:
 public function up() { 
 // Schema::create('libros', function (Blueprint $table) { 
 $table->bigIncrements('id');
 $table->string('nombre'); $table->string('precio');
 $table->timestamps(); });
 }
 
- php artisan migrate
- composer require laravel/ui
- php artisan ui bootstrap --auth
- npm install- npm run dev
- php artisan serve
- comprobar instalación http://127.0.0.1:8000/
- Seguir los pasos de https://github.com/awais-vteams/laravel-crud-generator
- composer require ibex/crud-generator --dev
- php artisan vendor:publish --tag=crud
- php artisan make:crud libros
- folder routes: web.php agregamos la ruta y que solo los usuarios autenticados vean el listado.

Route::get('/', function () { return view('welcome');});
Auth::routes();
Route::resource('libros', App\Http\Controllers\LibroController::class)->middleware('auth');
Route::get('/home', [App\Http\Controllers\HomeController::class, 'index'])->name('home');

- comprobamos que todo ok en http://127.0.0.1:8000/libros
- php artisan migrate:fresh --seed
- en folder routes: web.php 
Route::get('/', function () { return view('auth.login');});
