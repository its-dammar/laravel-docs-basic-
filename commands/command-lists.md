Here's list of Laravel Artisan commands:

### **1. General Artisan Commands**
- `php artisan list`  
  Lists all available Artisan commands.
  
- `php artisan help [command]`  
  Displays help for a specific command.

- `php artisan make:controller [ControllerName]`  
  Creates a new controller.

- `php artisan make:model [ModelName]`  
  Creates a new model.

- `php artisan make:migration [MigrationName]`  
  Creates a new migration file.

- `php artisan make:seeder [SeederName]`  
  Creates a new seeder.

- `php artisan make:middleware [MiddlewareName]`  
  Creates a new middleware.

- `php artisan make:request [RequestName]`  
  Creates a new form request class.

- `php artisan make:event [EventName]`  
  Creates a new event.

- `php artisan make:job [JobName]`  
  Creates a new job.

- `php artisan make:listener [ListenerName]`  
  Creates a new event listener.

- `php artisan make:factory [FactoryName]`  
  Creates a new model factory.

- `php artisan make:command [CommandName]`  
  Creates a custom Artisan command.

- `php artisan route:list`  
  Displays a list of all routes.

- `php artisan key:generate`  
  Generates a new application key.

- `php artisan env`  
  Displays the current application environment.

- `php artisan version`  
  Displays the current Laravel version.

- `php artisan serve`  
  Serves the application via a built-in PHP server.

- `php artisan config:clear`  
  Clears the configuration cache.

- `php artisan cache:clear`  
  Clears the application’s cache.

- `php artisan config:cache`  
  Caches the configuration files.

- `php artisan view:clear`  
  Clears the view cache.

- `php artisan route:cache`  
  Caches the routes.

- `php artisan optimize`  
  Optimizes the application for better performance.

- `php artisan optimize:clear`  
  Clears the cached optimized files.

### **2. Migration & Database Commands**
- `php artisan migrate`  
  Runs the database migrations.

- `php artisan migrate:rollback`  
  Rolls back the last migration operation.

- `php artisan migrate:reset`  
  Rolls back all migrations.

- `php artisan migrate:refresh`  
  Rolls back all migrations and re-runs them.

- `php artisan migrate:fresh`  
  Drops all tables and re-runs all migrations.

- `php artisan migrate:status`  
  Displays the status of each migration.

- `php artisan db:seed`  
  Runs the database seeders.

- `php artisan migrate:install`  
  Creates the migration repository.

- `php artisan migrate:rollback --step=[number]`  
  Rolls back a specific number of migrations.

- `php artisan migrate:refresh --seed`  
  Rolls back and re-runs migrations and seeds the database.

- `php artisan migrate:generate`  
  Generates migration files from an existing database schema.

### **3. Cache & Optimization Commands**
- `php artisan cache:clear`  
  Clears the application’s cache.

- `php artisan config:cache`  
  Caches the configuration files.

- `php artisan route:cache`  
  Caches the routes.

- `php artisan view:cache`  
  Compiles all Blade templates.

- `php artisan optimize`  
  Optimizes the application for better performance.

- `php artisan optimize:clear`  
  Clears all cached optimized files.

- `php artisan config:clear`  
  Clears the configuration cache.

- `php artisan route:clear`  
  Clears the route cache.

### **4. Queue Commands**
- `php artisan queue:work`  
  Processes the next job on the queue.

- `php artisan queue:listen`  
  Listens for queued jobs and processes them.

- `php artisan queue:restart`  
  Restarts all queue worker daemons.

- `php artisan queue:failed`  
  Lists all failed jobs.

- `php artisan queue:retry [job_id]`  
  Retries a specific failed job.

- `php artisan queue:flush`  
  Deletes all failed jobs.

### **5. Artisan Tinker**
- `php artisan tinker`  
  Opens an interactive shell to interact with your application and its database.

- `php artisan tinker --help`  
  Displays help for the Tinker command.

### **6. Testing Commands**
- `php artisan test`  
  Runs the application’s tests.

- `php artisan make:test [TestName]`  
  Creates a new test class.

- `php artisan test --filter=[test_name]`  
  Runs a specific test.

- `php artisan test --coverage`  
  Runs tests with code coverage information.

- `php artisan make:mock [MockName]`  
  Creates a mock for testing.

### **7. Authentication Commands**
- `php artisan make:auth`  
  Generates the authentication scaffolding.

- `php artisan auth:clear-resets`  
  Clears all expired password reset tokens.

### **8. Storage & Filesystem Commands**
- `php artisan storage:link`  
  Creates a symbolic link from public/storage to storage/app/public.

- `php artisan make:storage`  
  Creates a storage directory for your application.

### **9. Route Commands**
- `php artisan route:list`  
  Lists all registered routes.

- `php artisan route:cache`  
  Caches the application routes.

- `php artisan route:clear`  
  Clears the route cache.

### **10. Environment Commands**
- `php artisan env`  
  Displays the current application environment.

- `php artisan key:generate`  
  Generates a new application key.

### **11. Artisan Scheduler**
- `php artisan schedule:list`  
  Lists all scheduled tasks in the scheduler.

- `php artisan schedule:run`  
  Runs the scheduled tasks.

- `php artisan schedule:finish`  
  Marks a task as finished.

- `php artisan schedule:clear`  
  Clears the scheduled tasks.

### **12. Documentation Commands**
- `php artisan help [command]`  
  Displays help for a specific command.

- `php artisan list`  
  Lists all Artisan commands.

---

### **Shortcut Artisan Commands**
- `php artisan make:model [ModelName] -m`  
  Creates a model and its associated migration in one step.

- `php artisan make:controller [ControllerName] --resource`  
  Creates a resource controller (with default methods like index, show, etc.).

- `php artisan migrate:refresh --seed`  
  Rolls back migrations and re-runs them while seeding the database.

- `php artisan make:seeder [SeederName] --model=[ModelName]`  
  Creates a seeder bound to a specific model.

---

### **1. Model Command Variants**
- `php artisan make:model [ModelName]`  
  Creates a new model.

- `php artisan make:model [ModelName] -m`  
  Creates a new model with a migration file.

- `php artisan make:model [ModelName] -c`  
  Creates a new model with a controller.

- `php artisan make:model [ModelName] -f`  
  Creates a new model with a factory.

- `php artisan make:model [ModelName] -s`  
  Creates a new model with a seeder.

- `php artisan make:model [ModelName] -r`  
  Creates a new model with a resource controller.

- `php artisan make:model [ModelName] --all`  
  Creates a model, migration, controller, factory, and seeder.

- `php artisan make:model [ModelName] --controller --migration --resource`  
  Creates a model, controller, migration, and resource controller in one command.

- `php artisan make:model [ModelName] --factory --seeder`  
  Creates a model with a factory and seeder.

---

### **2. Controller Command Variants**
- `php artisan make:controller [ControllerName]`  
  Creates a new controller.

- `php artisan make:controller [ControllerName] --resource`  
  Creates a resource controller (includes methods like `index`, `show`, `create`, etc.).

- `php artisan make:controller [ControllerName] --model=[ModelName]`  
  Creates a controller with the specified model.

- `php artisan make:controller [ControllerName] --invokable`  
  Creates a controller with a single method (`__invoke`).

- `php artisan make:controller [ControllerName] --api`  
  Creates a controller with resource methods intended for API usage (no views).

- `php artisan make:controller [ControllerName] --middleware=[MiddlewareName]`  
  Creates a controller with specified middleware attached.

---

### **3. Migration Command Variants**
- `php artisan make:migration [MigrationName]`  
  Creates a new migration file.

- `php artisan make:migration [MigrationName] --create=[TableName]`  
  Creates a migration to create a table.

- `php artisan make:migration [MigrationName] --table=[TableName]`  
  Creates a migration to modify an existing table.

- `php artisan make:migration [MigrationName] --path=[Path]`  
  Creates a migration in a specific path.

- `php artisan make:migration [MigrationName] --fresh`  
  Creates a migration to reset the database before running the migration.

---

### **4. Seeder Command Variants**
- `php artisan make:

seeder [SeederName]`  
  Creates a new seeder class.

- `php artisan make:seeder [SeederName] --model=[ModelName]`  
  Creates a seeder that is bound to a specific model.

---
