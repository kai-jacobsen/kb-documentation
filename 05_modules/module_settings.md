*Modules*

## Settings

Each module class must have a static `$settings` array property. Most settings are optional resp. have a default value.  
Settings are not persistent.  
Changing settings affects all existing/already added modules (well, with one exception).


####Example

    use Kontentblocks\Modules\Module;
    
    class ModuleTextEditor extends Module
    {
        public static $settings = array(
            'name' => 'WP Editor',
            'publicName' => 'WP Editor',
            'id' => 'rich-text-editor',
            'description' => 'A WP Editor instance',
            'globalModule' => true,
            'views' => true,
            'connect' => array( 'normal', 'side', 'content-area' ),
            'controls' => array(
                'width' => 600
            ),
            'disabled' => false,
            'hidden' => false
    );
    
    
#### Required settings

##### (string) name

A human readable initial name for each instance of the module. Can be overridden by user input.

##### (string) publicName

A human readable persistent name for each instance of the module. Can not be changed by user input

##### (string) id

A slug-like identifier. Primarily used as additional css class on the module wrapper.

#### Optional

##### (string) description
A short description of the module.  

*default: ' '*

##### (bool) globalModule
Whether the module is available as a global module.  

*default: true*

##### (bool) views
Whether .twig files in the module root folder are detected as module templates.  
If enabled, a Module->View instance is automatically created.

*default: false*

##### (array) connect
Connect the module to all areas, specific areas or areas in a specific context.  
#####Possible values:
**'any'**: Make the module available to all registered areas  
**array**: array of area ids or context ids. Default available contexts are 'top', 'normal', 'side' and 'bottom'  
i.e. 'connect' => array('top', normal', 'content-area')  

*default: 'any'*

##### (array) controls

Settings for the frontend edit modal.

*default: ['width' => 450, 'fullscreen' => false]*

##### (bool) disabled

Deactivates the module. Already added instances still appear in areas but input and output is disabled.

*default:false*

##### (bool) hidden

Hide the module from all UIs.   
Primarily used for internal modules with special purposes.

*default: false*