## Namespacing in Plugins

Add to the top of PHP files:

`namespace something\somethingelse;`

When referencing your code outside of your namespace (such as when registering a function with Wordpress), refer to it 
in a manner similar to the following:

`register_activation_hook( __FILE__, __NAMESPACE__.'\\activate_my_plugin');`
