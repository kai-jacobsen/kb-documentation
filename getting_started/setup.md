# Setup

Just activating the plugin won't do anything unless the current theme actually **supports** 'kontentblocks'.

####kontentblocks.php

The plugin will look for `kontentblocks.php` in the root directory of the theme (child theme). If the file exists, `add_theme_support('kontentblocks')` gets called automatically. Another benifit of this convention is that we have a seperated file for plugin specific code.

So, first thing you need to do: create a `kontentblocks.php` in the themes root directory.

Afterwards you should notice a new admin menu item "Kontentblocks" with two submenu entries, ignore them for now.

###Folders

####/module-templates

The plugin will try to create a 'module-templates' folder in the root directory of your theme, and currently it relies on it's existence. If creation fails, please make sure to create that folder manually.

####Path to modules

Kontentblocks loads modules automatically and we need to make it aware of our locations.
A module path **must** be inside the wp-content (or custom content folder) location.  
To add a path, please copy the following to the kontentblocks.php file:

    add_filter(
        'kb.module.paths',
        function ( $paths ) {
            $paths[] = get_stylesheet_directory() . '/modules/';
            return $paths;
        }
    );
    
and make sure that the /modules directory exists in your theme directory.











