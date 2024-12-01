
### Step 1: Create a Route for Pagination

In `routes/web.php`, define a route to display paginated data. For example, to display posts:

```php
use App\Models\Post;

Route::get('/posts', function () {
    $posts = Post::paginate(10);  // 10 posts per page
    return view('posts.index', compact('posts'));
});
```

**Explanation**:  
- `paginate(10)` fetches 10 posts per page.
- `compact('posts')` passes the paginated posts to the view.

### Step 2: Display Paginated Data in a View

In `resources/views/posts/index.blade.php`, display the posts and pagination links:

```php
@foreach ($posts as $post)
    <p>{{ $post->title }}</p>
@endforeach

<!-- Display pagination links -->
{{ $posts->links() }}
```

**Explanation**:  
- `@foreach` loops through each post.
- `{{ $posts->links() }}` generates pagination links (next, previous, etc.).

### Step 3: Customize Pagination Per Page (Optional)

You can let users control how many items they want per page by using a query parameter (`per_page`). Modify the route as follows:

```php
Route::get('/posts', function () {
    $perPage = request()->get('per_page', 10);  // Default to 10 items per page
    $posts = Post::paginate($perPage);
    return view('posts.index', compact('posts'));
});
```

**Explanation**:  
- `request()->get('per_page', 10)` gets the `per_page` value from the URL (e.g., `/posts?per_page=20`), or defaults to 10.

### Step 4: Use Pagination in API Routes (Optional)

If you're building an API, you can paginate Eloquent results like this:

```php
Route::get('/api/posts', function () {
    return Post::paginate(10);  // Paginated posts in JSON format
});
```

**Explanation**:  
- This returns paginated posts as a JSON response, perfect for APIs.

### Step 5: Customize Pagination Links (Optional)

You can customize the appearance of pagination links by modifying the pagination views.

To publish the pagination views, run this command:

```bash
php artisan vendor:publish --tag=laravel-pagination
```

This will copy the pagination views to `resources/views/vendor/pagination`. You can then modify the default pagination style.

---
