# Areas

We're going to add two areas to the 'page' post type.  
Paste the following code to the kontentblocks.php file, as created in the previous step.

```
\Kontentblocks\registerArea(
    array(
        'id'              => 'demo-content', // unique id
        'name'            => 'Demo Page Content', // public name
        'description'     => 'A single demo area', // public description
        'postTypes'       => array( 'page' ), // array of post types 
        'context'         => 'normal', // location on the edit screen
    )
);```

```
\Kontentblocks\registerArea(
    array(
        'id'              => 'demo-sidebar', // unique id
        'name'            => 'Demo Page Sidebar', // public shown name
        'description'     => 'A single demo sidebar area', // public description
        'postTypes'       => array( 'page' ), // array of post types
        'context'         => 'side', // location on the edit screen
    )
);```

A full list of settings is available [@TODO].

After adding the code, create a new page and notice that the UI has changed.  
There are no modules yet to add, let's take care of it in the next section. 

#####Wait, the default editor is gone?

This is one of the few occasions when Kontentblocks does something you did not ask for, because it thinks you might like it that way.  

To bring the default editor on pages back, just add  
`add_filter('kb.remove.editor.page', '__return_false');`
to kontentblocks.php


