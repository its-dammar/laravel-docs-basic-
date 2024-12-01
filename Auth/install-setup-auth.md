To install and set up **authentication** in a Laravel application, you can use Laravel's built-in authentication features. Laravel offers several ways to implement authentication, and the most common method is using Laravel's **Auth** scaffolding and packages.

Here's a step-by-step guide to setting up **authentication** in Laravel:

**Normal Auth**
---
### **Laravel Auth Setup with Bootstrap**

1. **Install Laravel/UI**:  
   ```bash
   composer require laravel/ui
   ```

2. **Generate Auth with Bootstrap**:  
   ```bash
   php artisan ui bootstrap --auth
   ```

3. **Install Node.js**:  
   - Download from [Node.js Official Site](https://nodejs.org/).  

4. **Install Dependencies**:  
   ```bash
   npm install
   ```

5. **Compile Assets**:  
   ```bash
   npm run dev
   ```

6. **Run Migrations**:  
   ```bash
   php artisan migrate
   ```

7. **Start Server**:  
   ```bash
   php artisan serve
   ```

### **Access Auth Pages**  
- Login: `/login`  
- Register: `/register`  
- Password Reset: `/password/reset`
---

--------------------------------------------------------------------------------------------------------------

### Step 1: Install Laravel (If not already installed)

If you haven't already set up your Laravel project, you can do so by running:

```bash
composer create-project --prefer-dist laravel/laravel your-project-name
```

### Step 2: Install Laravel Breeze or Jetstream (Authentication Packages)

Laravel comes with several authentication packages like **Laravel Breeze**, **Laravel Jetstream**, and **Laravel Fortify**. 

- **Laravel Breeze**: A simple authentication starter kit that includes basic login, registration, password reset, and email verification.
- **Laravel Jetstream**: A more advanced authentication starter kit that includes features like two-factor authentication, team management, and session management.

Here, we will cover **Laravel Breeze**, which is lightweight and easy to get started with.

#### Option 1: Install Laravel Breeze

1. **Install Breeze Package**:

   You can install the Laravel Breeze package by running:

   ```bash
   composer require laravel/breeze --dev
   ```

2. **Install Breeze's Authentication Views and Routes**:

   Run the Breeze installation command:

   ```bash
   php artisan breeze:install
   ```

   This will generate the basic authentication views (login, register, etc.) in your `resources/views/auth` directory.

3. **Install Dependencies**:

   Next, install the front-end dependencies:

   ```bash
   npm install && npm run dev
   ```

   This will compile the front-end assets for the authentication views.

4. **Migrate Database**:

   Laravel's authentication requires a `users` table. Run the database migrations to create the necessary tables:

   ```bash
   php artisan migrate
   ```

5. **Serve the Application**:

   Run your Laravel application:

   ```bash
   php artisan serve
   ```

   Now, your application should have working authentication. You can visit the login and registration pages at `/login` and `/register`.

--------------------------------------------------------------------------------------------------------------


#### Option 2: Install Laravel Jetstream (For Advanced Features)

1. **Install Jetstream**:

   You can install **Jetstream** if you need additional features like team management and two-factor authentication:

   ```bash
   composer require laravel/jetstream
   ```

2. **Install Jetstream Scaffolding**:

   To install Jetstream with Livewire (a dynamic front-end framework) or Inertia.js (for Vue.js-based front-end), use one of the following commands:

   - For **Livewire** (Default):

   ```bash
   php artisan jetstream:install livewire
   ```

   - For **Inertia.js** (Vue.js):

   ```bash
   php artisan jetstream:install inertia
   ```

3. **Install Dependencies**:

   As with Breeze, you need to install the necessary NPM packages:

   ```bash
   npm install && npm run dev
   ```

4. **Migrate Database**:

   Run the migrations to create all the necessary tables, including `users`, `teams`, and other Jetstream-related tables.

   ```bash
   php artisan migrate
   ```

5. **Serve the Application**:

   After this, you can run the server:

   ```bash
   php artisan serve
   ```

6. **Access Authentication Pages**:

   You can access the login, registration, and two-factor authentication features on the `/login` and `/register` routes.

### Step 3: Authentication Routes and Views

Once the authentication scaffolding is set up, Laravel automatically generates authentication routes and views. You can modify them according to your needs.

#### Routes
By default, **Breeze** and **Jetstream** will set up routes like:

- `/login` - Login page
- `/register` - Registration page
- `/logout` - Logout route
- `/password/reset` - Password reset page
- `/email/verify` - Email verification page (if email verification is enabled)

You can view these routes by running:

```bash
php artisan route:list
```

### Step 4: Protect Routes with Authentication

To ensure that certain routes are only accessible to authenticated users, you can use the `auth` middleware in your routes file.

```php
// routes/web.php
use Illuminate\Support\Facades\Route;

Route::middleware(['auth'])->group(function () {
    Route::get('/dashboard', function () {
        return view('dashboard');
    });
});
```

This ensures that the `/dashboard` route is only accessible to logged-in users.

### Step 5: Customize Authentication Views

The default authentication views (login, register, etc.) are stored in `resources/views/auth`. You can customize these views to match your design.

For example, to customize the login page, modify `resources/views/auth/login.blade.php`.

### Step 6: Additional Configuration

- **Email Verification**: Laravel can send email verification links when a user registers. This is enabled by default in both **Breeze** and **Jetstream**. To enable email verification, make sure the `VerifyEmail` middleware is applied to the routes.

  You can customize this by editing `app/Http/Controllers/Auth/VerificationController.php`.

- **Two-Factor Authentication**: If you’re using **Jetstream** with two-factor authentication, users will have the option to enable or disable two-factor authentication on their profile page.

### Step 7: Installing Auth with Other Packages (Optional)

If you don’t want to use **Breeze** or **Jetstream**, you can use **Laravel Fortify** or other community-driven authentication packages.

#### Install Laravel Fortify:

1. **Install Fortify**:

   ```bash
   composer require laravel/fortify
   ```

2. **Publish the Fortify Configuration**:

   ```bash
   php artisan vendor:publish --provider="Laravel\Fortify\FortifyServiceProvider"
   ```

3. **Set up Routes and Views**:

   After installing Fortify, you need to register your routes and views. Fortify offers advanced authentication features like two-factor authentication and passwordless login.

4. **Migrate the Database**:

   ```bash
   php artisan migrate
   ```
