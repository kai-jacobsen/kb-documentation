*Modules*
## Naming Conventions & folder structure

The basic folder/file structure of a single module looks like this.

- ModuleMyFirstModule (folder)
    - ModuleMyFirstModule.php (file)

Each module must be a subclass of the Kontentblocks Module class.  
The class name must be the same as the name of the file and folder:

    ModuleMyFirstModule extends \Kontentblocks\Modules\Module
    
If you don't follow this convention your module gets ignored and does not appear in the system.

####Other files

A module can be enabled to be automatically connected to different (frontend) views. If enabled all .twig files in the module root folder are recognized as views. Other files and folder are ignored.

Learn more about Twig module templates and handling of module views.
