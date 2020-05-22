## Custom Meta Boxes

Custom fields are often needed for [Custom Post Types](/custom_post_types/README.md). You can give the user a place to 
enter and maintain custom fields with a custom meta box.

Note: most of what is here is taken directly from the Wordpress developer docs.

To define a custom meta box:

```php
add_meta_box(
    'my_meta_box_id',
    'My Meta Box Title',
    __NAMESPACE__.'\\my_meta_box_html',
    'my_custom_post_type'
);
```

This assumes that your CPT is already defined.

The hook is:

`add_action('add_meta_boxes', 'my_custom_meta_box');`

The HTML for the box is in the afore-referenced function:

```php
function my_meta_box_html($post) {
    ?>
    <label for="my_field">Description for this field</label>
    <select name="my_field" id="my_field" class="postbox">
        <option value="">Select something...</option>
        <option value="something">Something</option>
        <option value="else">Else</option>
    </select>
    <?php
}
```
