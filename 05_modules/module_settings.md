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
A s
*default: ' '*

##### (bool) globalModule
*default: true*

##### (bool) views
*default:false*
##### (array) connect
*default: 'any'*
##### (array) controls
*default: ['width' => 450, 'fullscreen' => false]*
##### (bool) disabled
*default:false*
##### (bool) hidden
*default: false*