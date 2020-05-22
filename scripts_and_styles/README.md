## Scripts and Styles

### Scripts

For scripts used within the WP dashboard:

```php
function my_admin_scripts() {
    wp_register_script( 'my-admin-js', plugins_url( 'my-plugin' ) . '/admin/js/my_admin.js', array( 'jquery' ));
    wp_localize_script( 'my-admin-js', 'myAjaxObj', 
        array( 'ajaxurl' => admin_url( 'admin-ajax.php' ),
            'someVariable' => 'some value',
        )
    );
    wp_enqueue_script( 'my-admin-js' );
}
add_action( 'admin_enqueue_scripts', __NAMESPACE__ . '\\my_admin_scripts' );
```
In the example above, "jQuery" is referenced. This is an example of how to tell Wordpress that your script has a dependency 
that Wordpress can provide.

Although localizing is normally for languages, it can also be used to globally declare JavaScript variables (such as with 
the example "some_variable" above.) Then, in our AJAX call, we can access it:

For scripts used on the front-end:

```php
function my_wp_scripts() {
    wp_register_script( 'my-public-js', plugins_url( 'my-plugin' ) . '/public/js/my_public.js', array( 'jquery' ));
    wp_enqueue_script( 'my-public-js' );
}
add_action( 'wp_enqueue_scripts', __NAMESPACE__ . '\\my_wp_scripts' );
```
### Styles

For styles used within the WP dashboard:

```php
function my_admin_styles() {
    wp_register_style( 'my-admin-css', plugins_url( 'my-plugin' ) . '/admin/css/my-admin.css' );
    wp_enqueue_style( 'my-admin-css' );
}
add_action( 'admin_enqueue_scripts', __NAMESPACE__ . '\\my_admin_styles' );
```

For styles used on the front-end:

```php
function my_wp_styles() {
    wp_register_style( 'my-public-css', plugins_url( 'my-plugin' ) . '/public/css/my-public.css' );
    wp_enqueue_style( 'my-public-css' );
}
add_action( 'wp_enqueue_scripts', __NAMESPACE__ . '\\my_wp_styles' );
```

Note that there is a separate `login_enqueue_scripts` action hook for the login screen.
