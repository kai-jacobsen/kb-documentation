## Path configuration

You need to setup at least one path where your modules exists.  
Only limitation: each path must be under whatever ```WP_CONTENT_DIR``` is set to.

To add one or multiple paths use this filter, for example:   

    /**
    * Filter to add custom paths to modules
    * @param $paths array of absolute paths
    * @return $paths array
    */
    add_filter(
        'kb.module.paths',
        function ( $paths ) {
            $paths[] = get_stylesheet_directory() . '/modules/';
            return $paths;
        }
    );
    

In that case the plugin will look in /themes/##theme-name##/modules/ for modules to load.  
More on folder structure and naming convention for modules 