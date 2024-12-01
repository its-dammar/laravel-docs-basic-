A complete step-by-step guide to creating a basic **CRUD application** in Laravel for managing tasks. This example starts from the beginning, ensuring that the application is functional and properly structured.

### Step 1: Install Laravel
If you haven't already installed Laravel, do so:
setup nodeJs 
```bash
1. composer create-project laravel/laravel laravel-crud  
OR
composer global require laravel/installer
laravel new example-app

2. cd example-app
npm install && npm run build
composer run dev

3. php artisan serve
```
Access the app in your browser at `http://localhost:8000`.

---

### Step 2: Set Up Database
Edit the `.env` file to configure the database:
```dotenv
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel_crud
DB_USERNAME=root
DB_PASSWORD=yourpassword
```

Create the database in MySQL:
```sql
CREATE DATABASE laravel_crud;
```

---

### Step 3: Create the Model, Migration, and Controller
Run the following Artisan command to generate resources:
```bash
php artisan make:model Task -mcr
```

This command creates:
- **Model:** `Task` (`app/Models/Task.php`)
- **Migration:** A new migration file in `database/migrations`.
- **Controller:** `TaskController` (`app/Http/Controllers/TaskController.php`).
- **Create model, controller and migration at a time** php artisan make:model [model_name] --controller --migration --resource

---

### Step 4: Define the Migration
Open the migration file under `database/migrations/` and define the schema:
```php
public function up()
{
    Schema::create('tasks', function (Blueprint $table) {
        $table->id();
        $table->string('title');
        $table->text('description')->nullable();
        $table->timestamps();
    });
}
```

Run the migration:
```bash
php artisan migrate
```

---

### Step 5: Define Routes
In `routes/web.php`, add routes for the Task resource:
```php
use App\Http\Controllers\TaskController;

Route::resource('tasks', TaskController::class);
```

---

### Step 6: Implement Controller Methods
In `app/Http/Controllers/TaskController.php`, fill in the methods:

```php
namespace App\Http\Controllers;

use App\Models\Task;
use Illuminate\Http\Request;

class TaskController extends Controller
{
    public function index()
    {
        $tasks = Task::all();
        return view('tasks.index', compact('tasks'));
    }

    public function create()
    {
        return view('tasks.create');
    }

    public function store(Request $request)
    {
        $request->validate([
            'title' => 'required|max:255',
            'description' => 'nullable'
        ]);

        Task::create($request->all());
        return redirect()->route('tasks.index')->with('success', 'Task created successfully.');
    }

    public function show(Task $task)
    {
        return view('tasks.show', compact('task'));
    }

    public function edit(Task $task)
    {
        return view('tasks.edit', compact('task'));
    }

    public function update(Request $request, Task $task)
    {
        $request->validate([
            'title' => 'required|max:255',
            'description' => 'nullable'
        ]);

        $task->update($request->all());
        return redirect()->route('tasks.index')->with('success', 'Task updated successfully.');
    }

    public function destroy(Task $task)
    {
        $task->delete();
        return redirect()->route('tasks.index')->with('success', 'Task deleted successfully.');
    }
}
```

---

### Step 7: Create Views
Under `resources/views/tasks/`, create the following **Blade templates**:

#### a. `index.blade.php`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Task List</title>
</head>
<body>
    <h1>Tasks</h1>
    <a href="{{ route('tasks.create') }}">Create New Task</a>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Title</th>
            <th>Description</th>
            <th>Actions</th>
        </tr>
        @foreach($tasks as $task)
        <tr>
            <td>{{ $task->id }}</td>
            <td>{{ $task->title }}</td>
            <td>{{ $task->description }}</td>
            <td>
                <a href="{{ route('tasks.show', $task->id) }}">View</a>
                <a href="{{ route('tasks.edit', $task->id) }}">Edit</a>
                <form action="{{ route('tasks.destroy', $task->id) }}" method="POST" style="display:inline;">
                    @csrf
                    @method('DELETE')
                    <button type="submit">Delete</button>
                </form>
            </td>
        </tr>
        @endforeach
    </table>
</body>
</html>
```

#### b. `create.blade.php`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Create Task</title>
</head>
<body>
    <h1>Create New Task</h1>
    <form action="{{ route('tasks.store') }}" method="POST">
        @csrf
        <label>Title:</label>
        <input type="text" name="title" required>
        <br>
        <label>Description:</label>
        <textarea name="description"></textarea>
        <br>
        <button type="submit">Save</button>
    </form>
    <a href="{{ route('tasks.index') }}">Back</a>
</body>
</html>
```

#### c. `show.blade.php`
```html
<!DOCTYPE html>
<html>
<head>
    <title>View Task</title>
</head>
<body>
    <h1>Task Details</h1>
    <p><strong>Title:</strong> {{ $task->title }}</p>
    <p><strong>Description:</strong> {{ $task->description }}</p>
    <a href="{{ route('tasks.index') }}">Back</a>
</body>
</html>
```

#### d. `edit.blade.php`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Edit Task</title>
</head>
<body>
    <h1>Edit Task</h1>
    <form action="{{ route('tasks.update', $task->id) }}" method="POST">
        @csrf
        @method('PUT')
        <label>Title:</label>
        <input type="text" name="title" value="{{ $task->title }}" required>
        <br>
        <label>Description:</label>
        <textarea name="description">{{ $task->description }}</textarea>
        <br>
        <button type="submit">Update</button>
    </form>
    <a href="{{ route('tasks.index') }}">Back</a>
</body>
</html>
```

---

### Step 8: Add Fillable Fields in Model
In `app/Models/Task.php`:
```php
protected $fillable = ['title', 'description'];
```

---

### Step 9: Test the Application
Run the server:
```bash
php artisan serve
```

Navigate to `http://localhost:8000/tasks` to see the task list and perform CRUD operations.