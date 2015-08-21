*Getting started*

## Theme Setup

This guide is based on a child theme for Twentfifteen.  
You can use any theme you want, but be aware that you have to change template files.

## Add theme support via kontentblocks.php

After plugin activation nothing has changed yet.  
First thing to do is to add theme support for Kontentblocks.

By adding a `kontentblocks.php` file to the root of your theme this happens automatically.  
If you want to do it manually just add `add_theme_support('kontentblocks')` to your bootstrap file ( functions.php, ...).

Throughout this guide,  all configuration code will go into the `kontentblocks.php` file.


## Configuration

Open your `kontentblocks.php` file and paste the following code to it:

```
<?php
// re-enable the standard editor for post-type 'page'
add_filter('kb.remove.editor.page', '__return_false');

// add a path to modules
add_filter(
    'kb.module.paths',
    function ( $paths ) {
        $paths[] = get_stylesheet_directory() . '/modules/';
        return $paths;
    }
);```


The first filter handles a special behavior:  
Kontentblocks removes the default editor from pages for convenience, that's the only reason.
To avoid confusion at the start, this first line brings it back.

The second filter adds a path to modules. The plugin will look in all registered paths for valid modules.  
A module path must be inside ```WP_CONTENT_DIR```. 

Next step: Adding areas.
