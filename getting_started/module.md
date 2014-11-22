# Module

We'll use the most efficient way to create our first module and module view handling by using all the good built-in stuff.  
Don't worry if you prefer to do things your own way, it's all there but I'd like to keep this 'quick'.


####Directories and Files

1. Go to your /modules directory and create a new directory, name it **ModuleDemoEditor**
2. Create a new .php file and give it the exact same name: **ModuleDemoEditor.php**
3. Open the file and paste this code:

```
<?php

use Kontentblocks\Modules\Module;
use Kontentblocks\Templating\ModuleView;


/**
 * Class ModuleDemoEditor
 */
class ModuleDemoEditor extends Module
{

    public static $defaults = array(
        'publicName' => 'Demo Editor',
        'name' => 'Demo Editor',
        'id' => 'demo-editor',
        'description' => 'Editors are all we need to create great content',
        'globallyAvailable' => true,
        'asTemplate' => true,
        'useViewLoader' => true,
        'connect' => array( 'normal', 'side' ),
        'controls' => array(
            'width' => 600
        )
    );

    /**
     * Backend, user-facing output must be echoed here
     */
    /*public function form()
    {
       We're using the built Fields API, which handles form creation by itself
    }*/


    /**
     * Whatever data should be stored for this module
     * must be returned here
     *
     * @param array $data actual $_POST data for this module
     * @param array $old previous data or empty array
     *
     * @return array
     *
     */
    /*public function save($data, $old)
    {
       We're using the built Fields API, which handles saving by itself
    }*/

    /**
    *
    * Whatever should be rendered on the frontend must
    * be returned here
    * @return null|string
    */
    public function render()
    {
        return $this->View->render();
    }
    
    /**
    * If the built-in Fields API is used, this is
    * the method to configure the FieldManager object of
    * the module ($this-Fields)
    * @return void
    */
    public function fields()
    {
        $this->Fields->addGroup( 'editor', array( 'label' => 'Editor' ) )
                     ->addField(
                         'editor', // field type
                         'democontent', // field key
                         array(
                             'label' => 'Editor',
                             'returnObj' => 'Element',
                             'the_content' => true, //apply filter
                             'conditions' => array(
                                 'areaContext' => array( 'normal' )
                             )
                         )
                     )
                     ->addField(
                         'textarea', // field type
                         'democontent_alt', // field key
                         array(
                             'label' => 'Textarea',
                             'returnObj' => 'Element',
                             'conditions' => array(
                                 'areaContext' => array( 'side' ) // only visible in 'side' area context
                             )
                         )
                     );
    }
}```

####$defaults

This static property defines the module settings, there are some more settings but we'll use the bare minimum here.  
Worth noting: settings are not persistent and can be changed anytime later.  

Let us look at the most important settings:

#####id

The id should be a unique slug-like string. It's part of the html class attribute of the module wrapper (frontend output), and the ViewLoader will look for a directory with that name. 

#####useViewLoader

If this setting is set to true (default: false) the so called ViewLoader will handle and load our module views (.twig templates) like this:  

It will look for .twig files in several locations, in this loading order:  
* module-templates/##id-of-module##/ (child theme)
* module-templates/##id-of-module##/ (parent theme)
* module class root directory 

In our case, it will look for all .twig files in:
* module-templates/demo-editor/
* modules/ModuleDemoEditor/

If a child theme provides a template with the same name in its /module-templates/demo-editor directory, that one will be used.

If it finds more than one unique template file, it will create a select field and the user can chose a template.  
If no viewfile is saved, it will always use the first in the collection (collection is sorted by filename, ascending).  

#####connect

This array can be filled with *area ids* or *area context ids* to define, where the module is available.  
We created two areas in the context of 'normal' and 'side', and our module will be available in both.  
We could have used the area ids 'demo-content' and 'demo-sidebar' as well. 

Changes to this setting won't affect already attached modules, it just removes them from the 'add module' menu.

###Methods

#####render()

Generally used to define the frontend output of the module.  
Output must be returned. This method should not echo anything.

In our example, the ViewLoader will setup a ModuleView (Twig Template object) instance automatically and we just need to call render on it.

We have no view yet, we will create one in the next section.

#####fields()

This is a special method and only used, if you want to use the built-in Fields API.  
If this method exists, a FieldManager object is created automatically and available through `$this->Fields`.  

Explaining the FieldManager is out of scope of this quick start tour, but basically you add groups and attach fields to those groups.

Groups are managed in tabs, if there are at least two groups.

If not using the Fields API, this method should not exist and the form() method should be used to create custom input forms.

In the above example, two fields are added but their visibility will depend on the area context of the module.  
If the module is attached to the 'demo-content' area, the 'editor' field is visible, if attached to the 'demo-sidebar' the 'textarea' field is visible.

If no conditionis set, a field is always visible. Other conditions are post-type, page-template and selected viewfile (when using the ViewLoader)

So in this case, if you move the module from one area to the other, different input forms will appear.
S

#####save() & form()

The Fields API will handle form creation and data saving for us.  
When using the fields() method, those methods should not exist in the child class, or you would have to call the appropiate methods on $Fields yourself.


####Done

Now you can open a page in the admin and add our first module to one or both areas.  
In the next two steps we create the views and integrated everything into the template file.

