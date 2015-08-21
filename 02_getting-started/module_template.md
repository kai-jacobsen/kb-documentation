*Getting Started*

##Create a front-end template for the module (using twig)

At this step, the demo module should look like this:
```
/**
 * Class ModuleDemo
 */
class ModuleDemo extends Module
{

    public static $settings = array(
        'publicName' => 'Demo Module',
        'name' => 'Demo Module',
        'views' => true,
        'connect' => array( 'normal' ),
        'id' => 'demo-module'
    );

    public function render()
    {
        return $this->view->render();
    }

    /**
     * fields configuration
     */
    public function fields()
    {

        /** @var FieldSection $group1 */
        $group1 = $this->fields->addGroup( 'editor', array( 'label' => 'Editor' ) );

        $group1->addField(
            'text', // field type
            'headline', // field key
            array(
                'label' => 'Headline',
                'std' => 'Lorem Ipsum'
            )
        );

        $group1->addField(
            'editor', // field type
            'longtext', // field key
            array(
                'label' => 'Editor',
                'media' => true,
                'std' => '<h2>Hello World</h2><p>Lorem Ipsum</p>'
            )
        );
    }

}```

**Please note** that the `views` setting of the module is set to `true`.  
This will enable a special behavior. The module will automatically look for `.twig` files inside of the module folder and collect them as possible templates. If there is more than one file, a select field will make the choices available.  
(There is a naming convention to limit templates to a specific context and/or force a certain order of appearance.)  

If there is only one template available, that one is used.

###Creating the view file



