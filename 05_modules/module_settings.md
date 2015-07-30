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
            'description' => 'A WP Editor instance',
            'globalModule' => true,
            'views' => true,
            'connect' => array( 'normal', 'side', 'content-area' ),
            'id' => 'rich-text-editor',
            'controls' => array(
                'width' => 600
            ),
            'disabled' => false,
            'hidden' => false
    );
    
    
#### Required settings

##### (string) name

##### (string) publicName

##### (string) id


#### Optional

