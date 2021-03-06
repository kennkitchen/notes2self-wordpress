## Custom Post Types

When creating a custom post type, create an array of labels such as the following (taken from the Wordpress docs):

```php
$labels = array(
    'name'                  => _x( 'Books', 'Post type general name', 'textdomain' ),
    'singular_name'         => _x( 'Book', 'Post type singular name', 'textdomain' ),
    'menu_name'             => _x( 'Books', 'Admin Menu text', 'textdomain' ),
    'name_admin_bar'        => _x( 'Book', 'Add New on Toolbar', 'textdomain' ),
    'add_new'               => __( 'Add New', 'textdomain' ),
    'add_new_item'          => __( 'Add New Book', 'textdomain' ),
    'new_item'              => __( 'New Book', 'textdomain' ),
    'edit_item'             => __( 'Edit Book', 'textdomain' ),
    'view_item'             => __( 'View Book', 'textdomain' ),
    'all_items'             => __( 'All Books', 'textdomain' ),
    'search_items'          => __( 'Search Books', 'textdomain' ),
    'parent_item_colon'     => __( 'Parent Books:', 'textdomain' ),
    'not_found'             => __( 'No books found.', 'textdomain' ),
    'not_found_in_trash'    => __( 'No books found in Trash.', 'textdomain' ),
    'featured_image'        => _x( 'Book Cover Image', 'Overrides the “Featured Image” phrase for this post type. Added in 4.3', 'textdomain' ),
    'set_featured_image'    => _x( 'Set cover image', 'Overrides the “Set featured image” phrase for this post type. Added in 4.3', 'textdomain' ),
    'remove_featured_image' => _x( 'Remove cover image', 'Overrides the “Remove featured image” phrase for this post type. Added in 4.3', 'textdomain' ),
    'use_featured_image'    => _x( 'Use as cover image', 'Overrides the “Use as featured image” phrase for this post type. Added in 4.3', 'textdomain' ),
    'archives'              => _x( 'Book archives', 'The post type archive label used in nav menus. Default “Post Archives”. Added in 4.4', 'textdomain' ),
    'insert_into_item'      => _x( 'Insert into book', 'Overrides the “Insert into post”/”Insert into page” phrase (used when inserting media into a post). Added in 4.4', 'textdomain' ),
    'uploaded_to_this_item' => _x( 'Uploaded to this book', 'Overrides the “Uploaded to this post”/”Uploaded to this page” phrase (used when viewing media attached to a post). Added in 4.4', 'textdomain' ),
    'filter_items_list'     => _x( 'Filter books list', 'Screen reader text for the filter links heading on the post type listing screen. Default “Filter posts list”/”Filter pages list”. Added in 4.4', 'textdomain' ),
    'items_list_navigation' => _x( 'Books list navigation', 'Screen reader text for the pagination heading on the post type listing screen. Default “Posts list navigation”/”Pages list navigation”. Added in 4.4', 'textdomain' ),
    'items_list'            => _x( 'Books list', 'Screen reader text for the items list heading on the post type listing screen. Default “Posts list”/”Pages list”. Added in 4.4', 'textdomain' ),
);
```
These are the terms that will be used when an instance of your CPT gets displayed.

The arguments for the call can be set up similar to the following:

```php
$args = array(
        'labels'             => $labels,
        'public'             => true,
        'menu_icon'          => 'dashicons-book',
        'publicly_queryable' => true,
        'show_ui'            => true,
        'show_in_menu'       => true,
        'query_var'          => true,
        'rewrite'            => array( 'slug' => 'book' ),
        'capability_type'    => 'post',
        'has_archive'        => true,
        'hierarchical'       => false,
        'menu_position'      => null,
        'supports'           => array( 'title', 'editor', 'author', 'thumbnail', 'excerpt', 'comments' ),
    );
```

Next, call the function to register the post type:

```register_post_type( 'book', $args );```

This should happen in an `init` hook, for example:

`add_action( 'init', __NAMESPACE__.'\\register_my_cpt' );`

See [Wordpress.org: Register Post Type](https://developer.wordpress.org/reference/functions/register_post_type/)
