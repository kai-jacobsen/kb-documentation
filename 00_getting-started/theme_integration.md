## Theme Support

Just activating the plugin won't do much, because it is mainly driven by code.  
First thing you need to do is to enable theme support.

#### Enable theme support by adding 'kontentblocks.php'

Adding a `kontentblocks.php` file to the root of your theme or child theme has  two benefits:

1. it automatically calls `add_theme_support('kontentblocks')`
2. Adding plugin related code to this file avoids undefined function errors when the plugin is not active


#### Manually adding theme support

If you don't like the idea of another file in your theme folder add the function call
`add_theme_support('kontentblocks')`  
to your own bootstrap file (i.e. functions.php)

In the next step you need to [configure loading paths](00_getting-started/path_configuration.md).
